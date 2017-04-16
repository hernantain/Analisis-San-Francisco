
Visualizaciones en el mapa de San Francisco
===========================================

.. code:: python

    import gmaps
    import pandas as pd
    import numpy as np 
    import seaborn as sns
    import matplotlib.pyplot as plt
    %matplotlib inline

.. code:: python

    gmaps.configure(api_key="AIzaSyAoCH3jhIkub2cHLRy2KcvOSQUPw1S9ERM")

.. code:: python

    trip_meta = pd.read_csv('data/trip.csv')
    stations_meta = pd.read_csv('data/station.csv')

Cuales son los viajes mas frecuentes entre estaciones?
======================================================

.. code:: python

    trip_meta2 = trip_meta[['start_station_name','end_station_name','duration']]
    trip_meta2 = trip_meta2.groupby(['start_station_name','end_station_name']).agg([np.size])
    trip_meta2 = pd.DataFrame(trip_meta2.to_records())
    trip_meta2.columns = ['start_station','end_station','trips']
    trip_meta2 = trip_meta2.sort_values('trips',ascending=False).head().reset_index()

.. code:: python

    origen = pd.merge(trip_meta2,stations_meta,how='left',left_on='start_station',right_on='name')

.. code:: python

    origen = origen[['start_station','end_station','trips','lat','long']]

.. code:: python

    origen_destino = pd.merge(origen,stations_meta,how='left',left_on='end_station',right_on='name')

.. code:: python

    origen_destino = origen_destino[['start_station','end_station','trips','lat_x','long_x','lat_y','long_y']]

TOP 5 viajes mas frecuentes
---------------------------

.. code:: python

    origen_destino.head()




.. raw:: html

    <div>
    <table border="1" class="dataframe">
      <thead>
        <tr style="text-align: right;">
          <th></th>
          <th>start_station</th>
          <th>end_station</th>
          <th>trips</th>
          <th>lat_x</th>
          <th>long_x</th>
          <th>lat_y</th>
          <th>long_y</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>0</th>
          <td>San Francisco Caltrain 2 (330 Townsend)</td>
          <td>Townsend at 7th</td>
          <td>6216</td>
          <td>37.776600</td>
          <td>-122.395470</td>
          <td>37.771058</td>
          <td>-122.402717</td>
        </tr>
        <tr>
          <th>1</th>
          <td>Harry Bridges Plaza (Ferry Building)</td>
          <td>Embarcadero at Sansome</td>
          <td>6164</td>
          <td>37.795392</td>
          <td>-122.394203</td>
          <td>37.804770</td>
          <td>-122.403234</td>
        </tr>
        <tr>
          <th>2</th>
          <td>Townsend at 7th</td>
          <td>San Francisco Caltrain (Townsend at 4th)</td>
          <td>5041</td>
          <td>37.771058</td>
          <td>-122.402717</td>
          <td>37.776617</td>
          <td>-122.395260</td>
        </tr>
        <tr>
          <th>3</th>
          <td>2nd at Townsend</td>
          <td>Harry Bridges Plaza (Ferry Building)</td>
          <td>4839</td>
          <td>37.780526</td>
          <td>-122.390288</td>
          <td>37.795392</td>
          <td>-122.394203</td>
        </tr>
        <tr>
          <th>4</th>
          <td>Harry Bridges Plaza (Ferry Building)</td>
          <td>2nd at Townsend</td>
          <td>4357</td>
          <td>37.795392</td>
          <td>-122.394203</td>
          <td>37.780526</td>
          <td>-122.390288</td>
        </tr>
      </tbody>
    </table>
    </div>



.. code:: python

    m = gmaps.Map()

.. code:: python

    def tuplas(a,b):
        return (a,b)

.. code:: python

    data1 = [tuplas(origen_destino.ix[0,'lat_x'],origen_destino.ix[0,'long_x']),\
             tuplas(origen_destino.ix[0,'lat_y'],origen_destino.ix[0,'long_y'])]
    data2 = [tuplas(origen_destino.ix[1,'lat_x'],origen_destino.ix[1,'long_x']),\
             tuplas(origen_destino.ix[1,'lat_y'],origen_destino.ix[1,'long_y'])]
    data3 = [tuplas(origen_destino.ix[2,'lat_x'],origen_destino.ix[2,'long_x']),\
             tuplas(origen_destino.ix[2,'lat_y'],origen_destino.ix[2,'long_y'])]
    data4 = [tuplas(origen_destino.ix[3,'lat_x'],origen_destino.ix[3,'long_x']),\
             tuplas(origen_destino.ix[3,'lat_y'],origen_destino.ix[3,'long_y'])]
    data5 = [tuplas(origen_destino.ix[4,'lat_x'],origen_destino.ix[4,'long_x']),\
             tuplas(origen_destino.ix[4,'lat_y'],origen_destino.ix[4,'long_y'])]

.. code:: python

    directions_layer1 = gmaps.Directions(data=data1)
    directions_layer2 = gmaps.Directions(data=data2)
    directions_layer3 = gmaps.Directions(data=data3)
    directions_layer4 = gmaps.Directions(data=data4)
    directions_layer5 = gmaps.Directions(data=data5)
    marker_layer2 = gmaps.marker_layer(stations_meta[['lat','long']],info_box_content=stations_meta['name'])

.. code:: python

    m.add_layer(directions_layer1)
    m.add_layer(directions_layer2)
    m.add_layer(directions_layer3)
    m.add_layer(directions_layer4)
    m.add_layer(directions_layer5)
    m.add_layer(marker_layer2)
    m


1er viaje mas frecuente:

.. image:: images/direction-layer1.png

2do viaje mas frecuente:

.. image:: images/direction-layer2.png

3er viaje mas frecuente:

.. image:: images/direction-layer3.png


Este ultima imagen corresponde al 4to y 5to viaje mas frecuente ida y vuelta(ver tabla):

.. image:: images/direction-layer4.png


Estaciones mas populares
========================

.. code:: python

    popular_stations = trip_meta[['start_station_name','duration']].groupby('start_station_name').size()
    popular_stations = pd.DataFrame(popular_stations)

.. code:: python

    popular_stations = pd.DataFrame(popular_stations.to_records())
    popular_stations = popular_stations[['start_station_name','0']]
    popular_stations.columns = ['station','trips']

.. code:: python

    popular_stations2 = pd.merge(popular_stations,stations_meta,how='inner',left_on='station',right_on='name')

.. code:: python

    popular_stations2[['station','trips','city']].sort_values('trips',ascending=False).head(15)




.. raw:: html

    <div>
    <table border="1" class="dataframe">
      <thead>
        <tr style="text-align: right;">
          <th></th>
          <th>station</th>
          <th>trips</th>
          <th>city</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>49</th>
          <td>San Francisco Caltrain (Townsend at 4th)</td>
          <td>49092</td>
          <td>San Francisco</td>
        </tr>
        <tr>
          <th>50</th>
          <td>San Francisco Caltrain 2 (330 Townsend)</td>
          <td>33742</td>
          <td>San Francisco</td>
        </tr>
        <tr>
          <th>23</th>
          <td>Harry Bridges Plaza (Ferry Building)</td>
          <td>32934</td>
          <td>San Francisco</td>
        </tr>
        <tr>
          <th>17</th>
          <td>Embarcadero at Sansome</td>
          <td>27713</td>
          <td>San Francisco</td>
        </tr>
        <tr>
          <th>65</th>
          <td>Temporary Transbay Terminal (Howard at Beale)</td>
          <td>26089</td>
          <td>San Francisco</td>
        </tr>
        <tr>
          <th>2</th>
          <td>2nd at Townsend</td>
          <td>25837</td>
          <td>San Francisco</td>
        </tr>
        <tr>
          <th>64</th>
          <td>Steuart at Market</td>
          <td>24838</td>
          <td>San Francisco</td>
        </tr>
        <tr>
          <th>29</th>
          <td>Market at Sansome</td>
          <td>24172</td>
          <td>San Francisco</td>
        </tr>
        <tr>
          <th>66</th>
          <td>Townsend at 7th</td>
          <td>23724</td>
          <td>San Francisco</td>
        </tr>
        <tr>
          <th>27</th>
          <td>Market at 10th</td>
          <td>20272</td>
          <td>San Francisco</td>
        </tr>
        <tr>
          <th>28</th>
          <td>Market at 4th</td>
          <td>20165</td>
          <td>San Francisco</td>
        </tr>
        <tr>
          <th>1</th>
          <td>2nd at South Park</td>
          <td>18496</td>
          <td>San Francisco</td>
        </tr>
        <tr>
          <th>38</th>
          <td>Powell Street BART</td>
          <td>18378</td>
          <td>San Francisco</td>
        </tr>
        <tr>
          <th>22</th>
          <td>Grant Avenue at Columbus Avenue</td>
          <td>16306</td>
          <td>San Francisco</td>
        </tr>
        <tr>
          <th>0</th>
          <td>2nd at Folsom</td>
          <td>15940</td>
          <td>San Francisco</td>
        </tr>
      </tbody>
    </table>
    </div>



.. code:: python

    heatmap_layer = gmaps.heatmap_layer(popular_stations2[['lat','long']],weights = popular_stations2['trips'],max_intensity=27000, point_radius=20.0)

.. code:: python

    marker_layer = gmaps.marker_layer(popular_stations2[['lat','long']],info_box_content=popular_stations2['station'])

.. code:: python

    n = gmaps.Map()

.. code:: python

    n.add_layer(heatmap_layer)
    n.add_layer(marker_layer)

.. code:: python

    n

Estaciones mas populares en San Jose
------------------------------------

.. code:: python

    popular_stations2.sort_values('trips',ascending=False).loc[popular_stations2.city == 'San Jose',:].head()




.. raw:: html

    <div>
    <table border="1" class="dataframe">
      <thead>
        <tr style="text-align: right;">
          <th></th>
          <th>station</th>
          <th>trips</th>
          <th>id</th>
          <th>name</th>
          <th>lat</th>
          <th>long</th>
          <th>dock_count</th>
          <th>city</th>
          <th>installation_date</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>54</th>
          <td>San Jose Diridon Caltrain Station</td>
          <td>9558</td>
          <td>2</td>
          <td>San Jose Diridon Caltrain Station</td>
          <td>37.329732</td>
          <td>-121.901782</td>
          <td>27</td>
          <td>San Jose</td>
          <td>8/6/2013</td>
        </tr>
        <tr>
          <th>59</th>
          <td>Santa Clara at Almaden</td>
          <td>3861</td>
          <td>4</td>
          <td>Santa Clara at Almaden</td>
          <td>37.333988</td>
          <td>-121.894902</td>
          <td>11</td>
          <td>San Jose</td>
          <td>8/6/2013</td>
        </tr>
        <tr>
          <th>56</th>
          <td>San Pedro Square</td>
          <td>2917</td>
          <td>6</td>
          <td>San Pedro Square</td>
          <td>37.336721</td>
          <td>-121.894074</td>
          <td>15</td>
          <td>San Jose</td>
          <td>8/7/2013</td>
        </tr>
        <tr>
          <th>52</th>
          <td>San Jose City Hall</td>
          <td>2393</td>
          <td>10</td>
          <td>San Jose City Hall</td>
          <td>37.337391</td>
          <td>-121.886995</td>
          <td>15</td>
          <td>San Jose</td>
          <td>8/6/2013</td>
        </tr>
        <tr>
          <th>36</th>
          <td>Paseo de San Antonio</td>
          <td>2233</td>
          <td>7</td>
          <td>Paseo de San Antonio</td>
          <td>37.333798</td>
          <td>-121.886943</td>
          <td>15</td>
          <td>San Jose</td>
          <td>8/7/2013</td>
        </tr>
      </tbody>
    </table>
    </div>



