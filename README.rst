
.. code:: python

    import gmaps
    import gmaps.datasets
    import pandas as pd
    import matplotlib.pyplot as plt
    import seaborn as sns
    import numpy as np

.. code:: python

    gmaps.configure(api_key="AIzaSyAoCH3jhIkub2cHLRy2KcvOSQUPw1S9ERM")

.. code:: python

    stations_meta = pd.read_csv('data/station.csv')

.. code:: python

    m = gmaps.Map()
    m.add_layer(gmaps.marker_layer(stations_meta[['lat','long']],info_box_content=stations_meta['name']))
    m

.. code:: python

    n = gmaps.Map()
    data = [(48.85341, 2.3488), (50.85045, 4.34878), (52.37403, 4.88969)]
    directions_layer = gmaps.Directions(data=data)
    n.add_layer(directions_layer)
    n

.. code:: python

    trip_meta = pd.read_csv('data/trip.csv')

.. code:: python

    trip_meta = trip_meta[['start_station_name','end_station_name']]

.. code:: python

    trip_meta




.. raw:: html

    <div>
    <table border="1" class="dataframe">
      <thead>
        <tr style="text-align: right;">
          <th></th>
          <th>start_station_name</th>
          <th>end_station_name</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>0</th>
          <td>South Van Ness at Market</td>
          <td>South Van Ness at Market</td>
        </tr>
        <tr>
          <th>1</th>
          <td>San Jose City Hall</td>
          <td>San Jose City Hall</td>
        </tr>
        <tr>
          <th>2</th>
          <td>Mountain View City Hall</td>
          <td>Mountain View City Hall</td>
        </tr>
        <tr>
          <th>3</th>
          <td>San Jose City Hall</td>
          <td>San Jose City Hall</td>
        </tr>
        <tr>
          <th>4</th>
          <td>South Van Ness at Market</td>
          <td>Market at 10th</td>
        </tr>
        <tr>
          <th>5</th>
          <td>Golden Gate at Polk</td>
          <td>Golden Gate at Polk</td>
        </tr>
        <tr>
          <th>6</th>
          <td>Santa Clara at Almaden</td>
          <td>Adobe on Almaden</td>
        </tr>
        <tr>
          <th>7</th>
          <td>San Salvador at 1st</td>
          <td>San Salvador at 1st</td>
        </tr>
        <tr>
          <th>8</th>
          <td>South Van Ness at Market</td>
          <td>South Van Ness at Market</td>
        </tr>
        <tr>
          <th>9</th>
          <td>San Jose City Hall</td>
          <td>MLK Library</td>
        </tr>
        <tr>
          <th>10</th>
          <td>Spear at Folsom</td>
          <td>Embarcadero at Bryant</td>
        </tr>
        <tr>
          <th>11</th>
          <td>San Pedro Square</td>
          <td>Santa Clara at Almaden</td>
        </tr>
        <tr>
          <th>12</th>
          <td>Mountain View Caltrain Station</td>
          <td>Mountain View Caltrain Station</td>
        </tr>
        <tr>
          <th>13</th>
          <td>2nd at South Park</td>
          <td>2nd at South Park</td>
        </tr>
        <tr>
          <th>14</th>
          <td>Clay at Battery</td>
          <td>Beale at Market</td>
        </tr>
        <tr>
          <th>15</th>
          <td>Post at Kearney</td>
          <td>Post at Kearney</td>
        </tr>
        <tr>
          <th>16</th>
          <td>San Jose City Hall</td>
          <td>San Jose City Hall</td>
        </tr>
        <tr>
          <th>17</th>
          <td>Market at 10th</td>
          <td>Market at 10th</td>
        </tr>
        <tr>
          <th>18</th>
          <td>Steuart at Market</td>
          <td>Harry Bridges Plaza (Ferry Building)</td>
        </tr>
        <tr>
          <th>19</th>
          <td>Powell Street BART</td>
          <td>Market at 4th</td>
        </tr>
        <tr>
          <th>20</th>
          <td>Spear at Folsom</td>
          <td>Embarcadero at Bryant</td>
        </tr>
        <tr>
          <th>21</th>
          <td>Redwood City Caltrain Station</td>
          <td>Redwood City Caltrain Station</td>
        </tr>
        <tr>
          <th>22</th>
          <td>San Francisco City Hall</td>
          <td>San Francisco City Hall</td>
        </tr>
        <tr>
          <th>23</th>
          <td>Post at Kearney</td>
          <td>Market at Sansome</td>
        </tr>
        <tr>
          <th>24</th>
          <td>Beale at Market</td>
          <td>Steuart at Market</td>
        </tr>
        <tr>
          <th>25</th>
          <td>Japantown</td>
          <td>Japantown</td>
        </tr>
        <tr>
          <th>26</th>
          <td>Temporary Transbay Terminal (Howard at Beale)</td>
          <td>Embarcadero at Folsom</td>
        </tr>
        <tr>
          <th>27</th>
          <td>San Jose Civic Center</td>
          <td>San Salvador at 1st</td>
        </tr>
        <tr>
          <th>28</th>
          <td>South Van Ness at Market</td>
          <td>South Van Ness at Market</td>
        </tr>
        <tr>
          <th>29</th>
          <td>Redwood City Medical Center</td>
          <td>Broadway at Main</td>
        </tr>
        <tr>
          <th>...</th>
          <td>...</td>
          <td>...</td>
        </tr>
        <tr>
          <th>669929</th>
          <td>Ryland Park</td>
          <td>San Jose Civic Center</td>
        </tr>
        <tr>
          <th>669930</th>
          <td>Market at 4th</td>
          <td>Powell at Post (Union Square)</td>
        </tr>
        <tr>
          <th>669931</th>
          <td>Market at 4th</td>
          <td>Powell at Post (Union Square)</td>
        </tr>
        <tr>
          <th>669932</th>
          <td>South Van Ness at Market</td>
          <td>Market at Sansome</td>
        </tr>
        <tr>
          <th>669933</th>
          <td>Market at 10th</td>
          <td>Powell Street BART</td>
        </tr>
        <tr>
          <th>669934</th>
          <td>Grant Avenue at Columbus Avenue</td>
          <td>Howard at 2nd</td>
        </tr>
        <tr>
          <th>669935</th>
          <td>Powell at Post (Union Square)</td>
          <td>Powell at Post (Union Square)</td>
        </tr>
        <tr>
          <th>669936</th>
          <td>Powell at Post (Union Square)</td>
          <td>Powell at Post (Union Square)</td>
        </tr>
        <tr>
          <th>669937</th>
          <td>Market at 4th</td>
          <td>San Francisco Caltrain (Townsend at 4th)</td>
        </tr>
        <tr>
          <th>669938</th>
          <td>Embarcadero at Vallejo</td>
          <td>Embarcadero at Sansome</td>
        </tr>
        <tr>
          <th>669939</th>
          <td>Market at 4th</td>
          <td>Embarcadero at Sansome</td>
        </tr>
        <tr>
          <th>669940</th>
          <td>Market at 4th</td>
          <td>Embarcadero at Sansome</td>
        </tr>
        <tr>
          <th>669941</th>
          <td>Davis at Jackson</td>
          <td>Davis at Jackson</td>
        </tr>
        <tr>
          <th>669942</th>
          <td>Embarcadero at Bryant</td>
          <td>Embarcadero at Sansome</td>
        </tr>
        <tr>
          <th>669943</th>
          <td>Market at 10th</td>
          <td>Powell Street BART</td>
        </tr>
        <tr>
          <th>669944</th>
          <td>Post at Kearny</td>
          <td>Market at Sansome</td>
        </tr>
        <tr>
          <th>669945</th>
          <td>Steuart at Market</td>
          <td>Embarcadero at Sansome</td>
        </tr>
        <tr>
          <th>669946</th>
          <td>Embarcadero at Folsom</td>
          <td>Harry Bridges Plaza (Ferry Building)</td>
        </tr>
        <tr>
          <th>669947</th>
          <td>Mountain View City Hall</td>
          <td>Mountain View City Hall</td>
        </tr>
        <tr>
          <th>669948</th>
          <td>Mountain View City Hall</td>
          <td>Mountain View City Hall</td>
        </tr>
        <tr>
          <th>669949</th>
          <td>Embarcadero at Bryant</td>
          <td>Embarcadero at Folsom</td>
        </tr>
        <tr>
          <th>669950</th>
          <td>Japantown</td>
          <td>Japantown</td>
        </tr>
        <tr>
          <th>669951</th>
          <td>Market at 10th</td>
          <td>Market at Sansome</td>
        </tr>
        <tr>
          <th>669952</th>
          <td>Yerba Buena Center of the Arts (3rd @ Howard)</td>
          <td>Steuart at Market</td>
        </tr>
        <tr>
          <th>669953</th>
          <td>South Van Ness at Market</td>
          <td>Civic Center BART (7th at Market)</td>
        </tr>
        <tr>
          <th>669954</th>
          <td>Powell Street BART</td>
          <td>Townsend at 7th</td>
        </tr>
        <tr>
          <th>669955</th>
          <td>Harry Bridges Plaza (Ferry Building)</td>
          <td>San Francisco Caltrain (Townsend at 4th)</td>
        </tr>
        <tr>
          <th>669956</th>
          <td>South Van Ness at Market</td>
          <td>5th at Howard</td>
        </tr>
        <tr>
          <th>669957</th>
          <td>South Van Ness at Market</td>
          <td>5th at Howard</td>
        </tr>
        <tr>
          <th>669958</th>
          <td>South Van Ness at Market</td>
          <td>5th at Howard</td>
        </tr>
      </tbody>
    </table>
    <p>669959 rows × 2 columns</p>
    </div>



.. code:: python

    trip_meta.info()


.. parsed-literal::

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 669959 entries, 0 to 669958
    Data columns (total 2 columns):
    start_station_name    669959 non-null object
    end_station_name      669959 non-null object
    dtypes: object(2)
    memory usage: 10.2+ MB


.. code:: python

    station_coord = stations_meta[['name','lat','long']]
    station_coord




.. raw:: html

    <div>
    <table border="1" class="dataframe">
      <thead>
        <tr style="text-align: right;">
          <th></th>
          <th>name</th>
          <th>lat</th>
          <th>long</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>0</th>
          <td>San Jose Diridon Caltrain Station</td>
          <td>37.329732</td>
          <td>-121.901782</td>
        </tr>
        <tr>
          <th>1</th>
          <td>San Jose Civic Center</td>
          <td>37.330698</td>
          <td>-121.888979</td>
        </tr>
        <tr>
          <th>2</th>
          <td>Santa Clara at Almaden</td>
          <td>37.333988</td>
          <td>-121.894902</td>
        </tr>
        <tr>
          <th>3</th>
          <td>Adobe on Almaden</td>
          <td>37.331415</td>
          <td>-121.893200</td>
        </tr>
        <tr>
          <th>4</th>
          <td>San Pedro Square</td>
          <td>37.336721</td>
          <td>-121.894074</td>
        </tr>
        <tr>
          <th>5</th>
          <td>Paseo de San Antonio</td>
          <td>37.333798</td>
          <td>-121.886943</td>
        </tr>
        <tr>
          <th>6</th>
          <td>San Salvador at 1st</td>
          <td>37.330165</td>
          <td>-121.885831</td>
        </tr>
        <tr>
          <th>7</th>
          <td>Japantown</td>
          <td>37.348742</td>
          <td>-121.894715</td>
        </tr>
        <tr>
          <th>8</th>
          <td>San Jose City Hall</td>
          <td>37.337391</td>
          <td>-121.886995</td>
        </tr>
        <tr>
          <th>9</th>
          <td>MLK Library</td>
          <td>37.335885</td>
          <td>-121.885660</td>
        </tr>
        <tr>
          <th>10</th>
          <td>SJSU 4th at San Carlos</td>
          <td>37.332808</td>
          <td>-121.883891</td>
        </tr>
        <tr>
          <th>11</th>
          <td>St James Park</td>
          <td>37.339301</td>
          <td>-121.889937</td>
        </tr>
        <tr>
          <th>12</th>
          <td>Arena Green / SAP Center</td>
          <td>37.332692</td>
          <td>-121.900084</td>
        </tr>
        <tr>
          <th>13</th>
          <td>SJSU - San Salvador at 9th</td>
          <td>37.333955</td>
          <td>-121.877349</td>
        </tr>
        <tr>
          <th>14</th>
          <td>Franklin at Maple</td>
          <td>37.481758</td>
          <td>-122.226904</td>
        </tr>
        <tr>
          <th>15</th>
          <td>Redwood City Caltrain Station</td>
          <td>37.486078</td>
          <td>-122.232089</td>
        </tr>
        <tr>
          <th>16</th>
          <td>San Mateo County Center</td>
          <td>37.487616</td>
          <td>-122.229951</td>
        </tr>
        <tr>
          <th>17</th>
          <td>Redwood City Public Library</td>
          <td>37.484219</td>
          <td>-122.227424</td>
        </tr>
        <tr>
          <th>18</th>
          <td>Stanford in Redwood City</td>
          <td>37.485370</td>
          <td>-122.203288</td>
        </tr>
        <tr>
          <th>19</th>
          <td>Redwood City Medical Center</td>
          <td>37.487682</td>
          <td>-122.223492</td>
        </tr>
        <tr>
          <th>20</th>
          <td>Mountain View City Hall</td>
          <td>37.389218</td>
          <td>-122.081896</td>
        </tr>
        <tr>
          <th>21</th>
          <td>Mountain View Caltrain Station</td>
          <td>37.394358</td>
          <td>-122.076713</td>
        </tr>
        <tr>
          <th>22</th>
          <td>San Antonio Caltrain Station</td>
          <td>37.406940</td>
          <td>-122.106758</td>
        </tr>
        <tr>
          <th>23</th>
          <td>Evelyn Park and Ride</td>
          <td>37.390277</td>
          <td>-122.066553</td>
        </tr>
        <tr>
          <th>24</th>
          <td>San Antonio Shopping Center</td>
          <td>37.400443</td>
          <td>-122.108338</td>
        </tr>
        <tr>
          <th>25</th>
          <td>Castro Street and El Camino Real</td>
          <td>37.385956</td>
          <td>-122.083678</td>
        </tr>
        <tr>
          <th>26</th>
          <td>Rengstorff Avenue / California Street</td>
          <td>37.400241</td>
          <td>-122.099076</td>
        </tr>
        <tr>
          <th>27</th>
          <td>Palo Alto Caltrain Station</td>
          <td>37.443988</td>
          <td>-122.164759</td>
        </tr>
        <tr>
          <th>28</th>
          <td>University and Emerson</td>
          <td>37.444521</td>
          <td>-122.163093</td>
        </tr>
        <tr>
          <th>29</th>
          <td>California Ave Caltrain Station</td>
          <td>37.429082</td>
          <td>-122.142805</td>
        </tr>
        <tr>
          <th>...</th>
          <td>...</td>
          <td>...</td>
          <td>...</td>
        </tr>
        <tr>
          <th>40</th>
          <td>Embarcadero at Folsom</td>
          <td>37.791464</td>
          <td>-122.391034</td>
        </tr>
        <tr>
          <th>41</th>
          <td>Powell Street BART</td>
          <td>37.783871</td>
          <td>-122.408433</td>
        </tr>
        <tr>
          <th>42</th>
          <td>Embarcadero at Bryant</td>
          <td>37.787152</td>
          <td>-122.388013</td>
        </tr>
        <tr>
          <th>43</th>
          <td>Temporary Transbay Terminal (Howard at Beale)</td>
          <td>37.789756</td>
          <td>-122.394643</td>
        </tr>
        <tr>
          <th>44</th>
          <td>Beale at Market</td>
          <td>37.792251</td>
          <td>-122.397086</td>
        </tr>
        <tr>
          <th>45</th>
          <td>5th at Howard</td>
          <td>37.781752</td>
          <td>-122.405127</td>
        </tr>
        <tr>
          <th>46</th>
          <td>San Francisco City Hall</td>
          <td>37.778650</td>
          <td>-122.418235</td>
        </tr>
        <tr>
          <th>47</th>
          <td>Golden Gate at Polk</td>
          <td>37.781332</td>
          <td>-122.418603</td>
        </tr>
        <tr>
          <th>48</th>
          <td>Embarcadero at Sansome</td>
          <td>37.804770</td>
          <td>-122.403234</td>
        </tr>
        <tr>
          <th>49</th>
          <td>2nd at Townsend</td>
          <td>37.780526</td>
          <td>-122.390288</td>
        </tr>
        <tr>
          <th>50</th>
          <td>2nd at Folsom</td>
          <td>37.785299</td>
          <td>-122.396236</td>
        </tr>
        <tr>
          <th>51</th>
          <td>Howard at 2nd</td>
          <td>37.786978</td>
          <td>-122.398108</td>
        </tr>
        <tr>
          <th>52</th>
          <td>2nd at South Park</td>
          <td>37.782259</td>
          <td>-122.392738</td>
        </tr>
        <tr>
          <th>53</th>
          <td>Townsend at 7th</td>
          <td>37.771058</td>
          <td>-122.402717</td>
        </tr>
        <tr>
          <th>54</th>
          <td>South Van Ness at Market</td>
          <td>37.774814</td>
          <td>-122.418954</td>
        </tr>
        <tr>
          <th>55</th>
          <td>Market at 10th</td>
          <td>37.776619</td>
          <td>-122.417385</td>
        </tr>
        <tr>
          <th>56</th>
          <td>Yerba Buena Center of the Arts (3rd @ Howard)</td>
          <td>37.784878</td>
          <td>-122.401014</td>
        </tr>
        <tr>
          <th>57</th>
          <td>San Francisco Caltrain 2 (330 Townsend)</td>
          <td>37.776600</td>
          <td>-122.395470</td>
        </tr>
        <tr>
          <th>58</th>
          <td>San Francisco Caltrain (Townsend at 4th)</td>
          <td>37.776617</td>
          <td>-122.395260</td>
        </tr>
        <tr>
          <th>59</th>
          <td>Powell at Post (Union Square)</td>
          <td>37.788446</td>
          <td>-122.408499</td>
        </tr>
        <tr>
          <th>60</th>
          <td>Civic Center BART (7th at Market)</td>
          <td>37.781039</td>
          <td>-122.411748</td>
        </tr>
        <tr>
          <th>61</th>
          <td>Grant Avenue at Columbus Avenue</td>
          <td>37.798522</td>
          <td>-122.407245</td>
        </tr>
        <tr>
          <th>62</th>
          <td>Steuart at Market</td>
          <td>37.794139</td>
          <td>-122.394434</td>
        </tr>
        <tr>
          <th>63</th>
          <td>Mechanics Plaza (Market at Battery)</td>
          <td>37.791300</td>
          <td>-122.399051</td>
        </tr>
        <tr>
          <th>64</th>
          <td>Market at 4th</td>
          <td>37.786305</td>
          <td>-122.404966</td>
        </tr>
        <tr>
          <th>65</th>
          <td>Market at Sansome</td>
          <td>37.789625</td>
          <td>-122.400811</td>
        </tr>
        <tr>
          <th>66</th>
          <td>Santa Clara County Civic Center</td>
          <td>37.352601</td>
          <td>-121.905733</td>
        </tr>
        <tr>
          <th>67</th>
          <td>Broadway St at Battery St</td>
          <td>37.798541</td>
          <td>-122.400862</td>
        </tr>
        <tr>
          <th>68</th>
          <td>Mezes Park</td>
          <td>37.491269</td>
          <td>-122.236234</td>
        </tr>
        <tr>
          <th>69</th>
          <td>Ryland Park</td>
          <td>37.342725</td>
          <td>-121.895617</td>
        </tr>
      </tbody>
    </table>
    <p>70 rows × 3 columns</p>
    </div>



.. code:: python

    trips_coord = pd.merge(trip_meta,station_coord,how='left',left_on='start_station_name',right_on='name')

.. code:: python

    trips_coord.info()


.. parsed-literal::

    <class 'pandas.core.frame.DataFrame'>
    Int64Index: 669959 entries, 0 to 669958
    Data columns (total 5 columns):
    start_station_name    669959 non-null object
    end_station_name      669959 non-null object
    name                  658617 non-null object
    lat                   658617 non-null float64
    long                  658617 non-null float64
    dtypes: float64(2), object(3)
    memory usage: 30.7+ MB


.. code:: python

    trips_coord




.. raw:: html

    <div>
    <table border="1" class="dataframe">
      <thead>
        <tr style="text-align: right;">
          <th></th>
          <th>start_station_name</th>
          <th>end_station_name</th>
          <th>name</th>
          <th>lat</th>
          <th>long</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>0</th>
          <td>South Van Ness at Market</td>
          <td>South Van Ness at Market</td>
          <td>South Van Ness at Market</td>
          <td>37.774814</td>
          <td>-122.418954</td>
        </tr>
        <tr>
          <th>1</th>
          <td>San Jose City Hall</td>
          <td>San Jose City Hall</td>
          <td>San Jose City Hall</td>
          <td>37.337391</td>
          <td>-121.886995</td>
        </tr>
        <tr>
          <th>2</th>
          <td>Mountain View City Hall</td>
          <td>Mountain View City Hall</td>
          <td>Mountain View City Hall</td>
          <td>37.389218</td>
          <td>-122.081896</td>
        </tr>
        <tr>
          <th>3</th>
          <td>San Jose City Hall</td>
          <td>San Jose City Hall</td>
          <td>San Jose City Hall</td>
          <td>37.337391</td>
          <td>-121.886995</td>
        </tr>
        <tr>
          <th>4</th>
          <td>South Van Ness at Market</td>
          <td>Market at 10th</td>
          <td>South Van Ness at Market</td>
          <td>37.774814</td>
          <td>-122.418954</td>
        </tr>
        <tr>
          <th>5</th>
          <td>Golden Gate at Polk</td>
          <td>Golden Gate at Polk</td>
          <td>Golden Gate at Polk</td>
          <td>37.781332</td>
          <td>-122.418603</td>
        </tr>
        <tr>
          <th>6</th>
          <td>Santa Clara at Almaden</td>
          <td>Adobe on Almaden</td>
          <td>Santa Clara at Almaden</td>
          <td>37.333988</td>
          <td>-121.894902</td>
        </tr>
        <tr>
          <th>7</th>
          <td>San Salvador at 1st</td>
          <td>San Salvador at 1st</td>
          <td>San Salvador at 1st</td>
          <td>37.330165</td>
          <td>-121.885831</td>
        </tr>
        <tr>
          <th>8</th>
          <td>South Van Ness at Market</td>
          <td>South Van Ness at Market</td>
          <td>South Van Ness at Market</td>
          <td>37.774814</td>
          <td>-122.418954</td>
        </tr>
        <tr>
          <th>9</th>
          <td>San Jose City Hall</td>
          <td>MLK Library</td>
          <td>San Jose City Hall</td>
          <td>37.337391</td>
          <td>-121.886995</td>
        </tr>
        <tr>
          <th>10</th>
          <td>Spear at Folsom</td>
          <td>Embarcadero at Bryant</td>
          <td>Spear at Folsom</td>
          <td>37.790302</td>
          <td>-122.390637</td>
        </tr>
        <tr>
          <th>11</th>
          <td>San Pedro Square</td>
          <td>Santa Clara at Almaden</td>
          <td>San Pedro Square</td>
          <td>37.336721</td>
          <td>-121.894074</td>
        </tr>
        <tr>
          <th>12</th>
          <td>Mountain View Caltrain Station</td>
          <td>Mountain View Caltrain Station</td>
          <td>Mountain View Caltrain Station</td>
          <td>37.394358</td>
          <td>-122.076713</td>
        </tr>
        <tr>
          <th>13</th>
          <td>2nd at South Park</td>
          <td>2nd at South Park</td>
          <td>2nd at South Park</td>
          <td>37.782259</td>
          <td>-122.392738</td>
        </tr>
        <tr>
          <th>14</th>
          <td>Clay at Battery</td>
          <td>Beale at Market</td>
          <td>Clay at Battery</td>
          <td>37.795001</td>
          <td>-122.399970</td>
        </tr>
        <tr>
          <th>15</th>
          <td>Post at Kearney</td>
          <td>Post at Kearney</td>
          <td>Post at Kearney</td>
          <td>37.788975</td>
          <td>-122.403452</td>
        </tr>
        <tr>
          <th>16</th>
          <td>San Jose City Hall</td>
          <td>San Jose City Hall</td>
          <td>San Jose City Hall</td>
          <td>37.337391</td>
          <td>-121.886995</td>
        </tr>
        <tr>
          <th>17</th>
          <td>Market at 10th</td>
          <td>Market at 10th</td>
          <td>Market at 10th</td>
          <td>37.776619</td>
          <td>-122.417385</td>
        </tr>
        <tr>
          <th>18</th>
          <td>Steuart at Market</td>
          <td>Harry Bridges Plaza (Ferry Building)</td>
          <td>Steuart at Market</td>
          <td>37.794139</td>
          <td>-122.394434</td>
        </tr>
        <tr>
          <th>19</th>
          <td>Powell Street BART</td>
          <td>Market at 4th</td>
          <td>Powell Street BART</td>
          <td>37.783871</td>
          <td>-122.408433</td>
        </tr>
        <tr>
          <th>20</th>
          <td>Spear at Folsom</td>
          <td>Embarcadero at Bryant</td>
          <td>Spear at Folsom</td>
          <td>37.790302</td>
          <td>-122.390637</td>
        </tr>
        <tr>
          <th>21</th>
          <td>Redwood City Caltrain Station</td>
          <td>Redwood City Caltrain Station</td>
          <td>Redwood City Caltrain Station</td>
          <td>37.486078</td>
          <td>-122.232089</td>
        </tr>
        <tr>
          <th>22</th>
          <td>San Francisco City Hall</td>
          <td>San Francisco City Hall</td>
          <td>San Francisco City Hall</td>
          <td>37.778650</td>
          <td>-122.418235</td>
        </tr>
        <tr>
          <th>23</th>
          <td>Post at Kearney</td>
          <td>Market at Sansome</td>
          <td>Post at Kearney</td>
          <td>37.788975</td>
          <td>-122.403452</td>
        </tr>
        <tr>
          <th>24</th>
          <td>Beale at Market</td>
          <td>Steuart at Market</td>
          <td>Beale at Market</td>
          <td>37.792251</td>
          <td>-122.397086</td>
        </tr>
        <tr>
          <th>25</th>
          <td>Japantown</td>
          <td>Japantown</td>
          <td>Japantown</td>
          <td>37.348742</td>
          <td>-121.894715</td>
        </tr>
        <tr>
          <th>26</th>
          <td>Temporary Transbay Terminal (Howard at Beale)</td>
          <td>Embarcadero at Folsom</td>
          <td>Temporary Transbay Terminal (Howard at Beale)</td>
          <td>37.789756</td>
          <td>-122.394643</td>
        </tr>
        <tr>
          <th>27</th>
          <td>San Jose Civic Center</td>
          <td>San Salvador at 1st</td>
          <td>San Jose Civic Center</td>
          <td>37.330698</td>
          <td>-121.888979</td>
        </tr>
        <tr>
          <th>28</th>
          <td>South Van Ness at Market</td>
          <td>South Van Ness at Market</td>
          <td>South Van Ness at Market</td>
          <td>37.774814</td>
          <td>-122.418954</td>
        </tr>
        <tr>
          <th>29</th>
          <td>Redwood City Medical Center</td>
          <td>Broadway at Main</td>
          <td>Redwood City Medical Center</td>
          <td>37.487682</td>
          <td>-122.223492</td>
        </tr>
        <tr>
          <th>...</th>
          <td>...</td>
          <td>...</td>
          <td>...</td>
          <td>...</td>
          <td>...</td>
        </tr>
        <tr>
          <th>669929</th>
          <td>Ryland Park</td>
          <td>San Jose Civic Center</td>
          <td>Ryland Park</td>
          <td>37.342725</td>
          <td>-121.895617</td>
        </tr>
        <tr>
          <th>669930</th>
          <td>Market at 4th</td>
          <td>Powell at Post (Union Square)</td>
          <td>Market at 4th</td>
          <td>37.786305</td>
          <td>-122.404966</td>
        </tr>
        <tr>
          <th>669931</th>
          <td>Market at 4th</td>
          <td>Powell at Post (Union Square)</td>
          <td>Market at 4th</td>
          <td>37.786305</td>
          <td>-122.404966</td>
        </tr>
        <tr>
          <th>669932</th>
          <td>South Van Ness at Market</td>
          <td>Market at Sansome</td>
          <td>South Van Ness at Market</td>
          <td>37.774814</td>
          <td>-122.418954</td>
        </tr>
        <tr>
          <th>669933</th>
          <td>Market at 10th</td>
          <td>Powell Street BART</td>
          <td>Market at 10th</td>
          <td>37.776619</td>
          <td>-122.417385</td>
        </tr>
        <tr>
          <th>669934</th>
          <td>Grant Avenue at Columbus Avenue</td>
          <td>Howard at 2nd</td>
          <td>Grant Avenue at Columbus Avenue</td>
          <td>37.798522</td>
          <td>-122.407245</td>
        </tr>
        <tr>
          <th>669935</th>
          <td>Powell at Post (Union Square)</td>
          <td>Powell at Post (Union Square)</td>
          <td>Powell at Post (Union Square)</td>
          <td>37.788446</td>
          <td>-122.408499</td>
        </tr>
        <tr>
          <th>669936</th>
          <td>Powell at Post (Union Square)</td>
          <td>Powell at Post (Union Square)</td>
          <td>Powell at Post (Union Square)</td>
          <td>37.788446</td>
          <td>-122.408499</td>
        </tr>
        <tr>
          <th>669937</th>
          <td>Market at 4th</td>
          <td>San Francisco Caltrain (Townsend at 4th)</td>
          <td>Market at 4th</td>
          <td>37.786305</td>
          <td>-122.404966</td>
        </tr>
        <tr>
          <th>669938</th>
          <td>Embarcadero at Vallejo</td>
          <td>Embarcadero at Sansome</td>
          <td>Embarcadero at Vallejo</td>
          <td>37.799953</td>
          <td>-122.398525</td>
        </tr>
        <tr>
          <th>669939</th>
          <td>Market at 4th</td>
          <td>Embarcadero at Sansome</td>
          <td>Market at 4th</td>
          <td>37.786305</td>
          <td>-122.404966</td>
        </tr>
        <tr>
          <th>669940</th>
          <td>Market at 4th</td>
          <td>Embarcadero at Sansome</td>
          <td>Market at 4th</td>
          <td>37.786305</td>
          <td>-122.404966</td>
        </tr>
        <tr>
          <th>669941</th>
          <td>Davis at Jackson</td>
          <td>Davis at Jackson</td>
          <td>Davis at Jackson</td>
          <td>37.797280</td>
          <td>-122.398436</td>
        </tr>
        <tr>
          <th>669942</th>
          <td>Embarcadero at Bryant</td>
          <td>Embarcadero at Sansome</td>
          <td>Embarcadero at Bryant</td>
          <td>37.787152</td>
          <td>-122.388013</td>
        </tr>
        <tr>
          <th>669943</th>
          <td>Market at 10th</td>
          <td>Powell Street BART</td>
          <td>Market at 10th</td>
          <td>37.776619</td>
          <td>-122.417385</td>
        </tr>
        <tr>
          <th>669944</th>
          <td>Post at Kearny</td>
          <td>Market at Sansome</td>
          <td>NaN</td>
          <td>NaN</td>
          <td>NaN</td>
        </tr>
        <tr>
          <th>669945</th>
          <td>Steuart at Market</td>
          <td>Embarcadero at Sansome</td>
          <td>Steuart at Market</td>
          <td>37.794139</td>
          <td>-122.394434</td>
        </tr>
        <tr>
          <th>669946</th>
          <td>Embarcadero at Folsom</td>
          <td>Harry Bridges Plaza (Ferry Building)</td>
          <td>Embarcadero at Folsom</td>
          <td>37.791464</td>
          <td>-122.391034</td>
        </tr>
        <tr>
          <th>669947</th>
          <td>Mountain View City Hall</td>
          <td>Mountain View City Hall</td>
          <td>Mountain View City Hall</td>
          <td>37.389218</td>
          <td>-122.081896</td>
        </tr>
        <tr>
          <th>669948</th>
          <td>Mountain View City Hall</td>
          <td>Mountain View City Hall</td>
          <td>Mountain View City Hall</td>
          <td>37.389218</td>
          <td>-122.081896</td>
        </tr>
        <tr>
          <th>669949</th>
          <td>Embarcadero at Bryant</td>
          <td>Embarcadero at Folsom</td>
          <td>Embarcadero at Bryant</td>
          <td>37.787152</td>
          <td>-122.388013</td>
        </tr>
        <tr>
          <th>669950</th>
          <td>Japantown</td>
          <td>Japantown</td>
          <td>Japantown</td>
          <td>37.348742</td>
          <td>-121.894715</td>
        </tr>
        <tr>
          <th>669951</th>
          <td>Market at 10th</td>
          <td>Market at Sansome</td>
          <td>Market at 10th</td>
          <td>37.776619</td>
          <td>-122.417385</td>
        </tr>
        <tr>
          <th>669952</th>
          <td>Yerba Buena Center of the Arts (3rd @ Howard)</td>
          <td>Steuart at Market</td>
          <td>Yerba Buena Center of the Arts (3rd @ Howard)</td>
          <td>37.784878</td>
          <td>-122.401014</td>
        </tr>
        <tr>
          <th>669953</th>
          <td>South Van Ness at Market</td>
          <td>Civic Center BART (7th at Market)</td>
          <td>South Van Ness at Market</td>
          <td>37.774814</td>
          <td>-122.418954</td>
        </tr>
        <tr>
          <th>669954</th>
          <td>Powell Street BART</td>
          <td>Townsend at 7th</td>
          <td>Powell Street BART</td>
          <td>37.783871</td>
          <td>-122.408433</td>
        </tr>
        <tr>
          <th>669955</th>
          <td>Harry Bridges Plaza (Ferry Building)</td>
          <td>San Francisco Caltrain (Townsend at 4th)</td>
          <td>Harry Bridges Plaza (Ferry Building)</td>
          <td>37.795392</td>
          <td>-122.394203</td>
        </tr>
        <tr>
          <th>669956</th>
          <td>South Van Ness at Market</td>
          <td>5th at Howard</td>
          <td>South Van Ness at Market</td>
          <td>37.774814</td>
          <td>-122.418954</td>
        </tr>
        <tr>
          <th>669957</th>
          <td>South Van Ness at Market</td>
          <td>5th at Howard</td>
          <td>South Van Ness at Market</td>
          <td>37.774814</td>
          <td>-122.418954</td>
        </tr>
        <tr>
          <th>669958</th>
          <td>South Van Ness at Market</td>
          <td>5th at Howard</td>
          <td>South Van Ness at Market</td>
          <td>37.774814</td>
          <td>-122.418954</td>
        </tr>
      </tbody>
    </table>
    <p>669959 rows × 5 columns</p>
    </div>



.. code:: python

    trips_coord = trips_coord[['start_station_name','end_station_name','lat','long']]
    trips_coord.columns = ['start_station','end_station','start_lat','start_long']
    trips_coord




.. raw:: html

    <div>
    <table border="1" class="dataframe">
      <thead>
        <tr style="text-align: right;">
          <th></th>
          <th>start_station</th>
          <th>end_station</th>
          <th>start_lat</th>
          <th>start_long</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>0</th>
          <td>South Van Ness at Market</td>
          <td>South Van Ness at Market</td>
          <td>37.774814</td>
          <td>-122.418954</td>
        </tr>
        <tr>
          <th>1</th>
          <td>San Jose City Hall</td>
          <td>San Jose City Hall</td>
          <td>37.337391</td>
          <td>-121.886995</td>
        </tr>
        <tr>
          <th>2</th>
          <td>Mountain View City Hall</td>
          <td>Mountain View City Hall</td>
          <td>37.389218</td>
          <td>-122.081896</td>
        </tr>
        <tr>
          <th>3</th>
          <td>San Jose City Hall</td>
          <td>San Jose City Hall</td>
          <td>37.337391</td>
          <td>-121.886995</td>
        </tr>
        <tr>
          <th>4</th>
          <td>South Van Ness at Market</td>
          <td>Market at 10th</td>
          <td>37.774814</td>
          <td>-122.418954</td>
        </tr>
        <tr>
          <th>5</th>
          <td>Golden Gate at Polk</td>
          <td>Golden Gate at Polk</td>
          <td>37.781332</td>
          <td>-122.418603</td>
        </tr>
        <tr>
          <th>6</th>
          <td>Santa Clara at Almaden</td>
          <td>Adobe on Almaden</td>
          <td>37.333988</td>
          <td>-121.894902</td>
        </tr>
        <tr>
          <th>7</th>
          <td>San Salvador at 1st</td>
          <td>San Salvador at 1st</td>
          <td>37.330165</td>
          <td>-121.885831</td>
        </tr>
        <tr>
          <th>8</th>
          <td>South Van Ness at Market</td>
          <td>South Van Ness at Market</td>
          <td>37.774814</td>
          <td>-122.418954</td>
        </tr>
        <tr>
          <th>9</th>
          <td>San Jose City Hall</td>
          <td>MLK Library</td>
          <td>37.337391</td>
          <td>-121.886995</td>
        </tr>
        <tr>
          <th>10</th>
          <td>Spear at Folsom</td>
          <td>Embarcadero at Bryant</td>
          <td>37.790302</td>
          <td>-122.390637</td>
        </tr>
        <tr>
          <th>11</th>
          <td>San Pedro Square</td>
          <td>Santa Clara at Almaden</td>
          <td>37.336721</td>
          <td>-121.894074</td>
        </tr>
        <tr>
          <th>12</th>
          <td>Mountain View Caltrain Station</td>
          <td>Mountain View Caltrain Station</td>
          <td>37.394358</td>
          <td>-122.076713</td>
        </tr>
        <tr>
          <th>13</th>
          <td>2nd at South Park</td>
          <td>2nd at South Park</td>
          <td>37.782259</td>
          <td>-122.392738</td>
        </tr>
        <tr>
          <th>14</th>
          <td>Clay at Battery</td>
          <td>Beale at Market</td>
          <td>37.795001</td>
          <td>-122.399970</td>
        </tr>
        <tr>
          <th>15</th>
          <td>Post at Kearney</td>
          <td>Post at Kearney</td>
          <td>37.788975</td>
          <td>-122.403452</td>
        </tr>
        <tr>
          <th>16</th>
          <td>San Jose City Hall</td>
          <td>San Jose City Hall</td>
          <td>37.337391</td>
          <td>-121.886995</td>
        </tr>
        <tr>
          <th>17</th>
          <td>Market at 10th</td>
          <td>Market at 10th</td>
          <td>37.776619</td>
          <td>-122.417385</td>
        </tr>
        <tr>
          <th>18</th>
          <td>Steuart at Market</td>
          <td>Harry Bridges Plaza (Ferry Building)</td>
          <td>37.794139</td>
          <td>-122.394434</td>
        </tr>
        <tr>
          <th>19</th>
          <td>Powell Street BART</td>
          <td>Market at 4th</td>
          <td>37.783871</td>
          <td>-122.408433</td>
        </tr>
        <tr>
          <th>20</th>
          <td>Spear at Folsom</td>
          <td>Embarcadero at Bryant</td>
          <td>37.790302</td>
          <td>-122.390637</td>
        </tr>
        <tr>
          <th>21</th>
          <td>Redwood City Caltrain Station</td>
          <td>Redwood City Caltrain Station</td>
          <td>37.486078</td>
          <td>-122.232089</td>
        </tr>
        <tr>
          <th>22</th>
          <td>San Francisco City Hall</td>
          <td>San Francisco City Hall</td>
          <td>37.778650</td>
          <td>-122.418235</td>
        </tr>
        <tr>
          <th>23</th>
          <td>Post at Kearney</td>
          <td>Market at Sansome</td>
          <td>37.788975</td>
          <td>-122.403452</td>
        </tr>
        <tr>
          <th>24</th>
          <td>Beale at Market</td>
          <td>Steuart at Market</td>
          <td>37.792251</td>
          <td>-122.397086</td>
        </tr>
        <tr>
          <th>25</th>
          <td>Japantown</td>
          <td>Japantown</td>
          <td>37.348742</td>
          <td>-121.894715</td>
        </tr>
        <tr>
          <th>26</th>
          <td>Temporary Transbay Terminal (Howard at Beale)</td>
          <td>Embarcadero at Folsom</td>
          <td>37.789756</td>
          <td>-122.394643</td>
        </tr>
        <tr>
          <th>27</th>
          <td>San Jose Civic Center</td>
          <td>San Salvador at 1st</td>
          <td>37.330698</td>
          <td>-121.888979</td>
        </tr>
        <tr>
          <th>28</th>
          <td>South Van Ness at Market</td>
          <td>South Van Ness at Market</td>
          <td>37.774814</td>
          <td>-122.418954</td>
        </tr>
        <tr>
          <th>29</th>
          <td>Redwood City Medical Center</td>
          <td>Broadway at Main</td>
          <td>37.487682</td>
          <td>-122.223492</td>
        </tr>
        <tr>
          <th>...</th>
          <td>...</td>
          <td>...</td>
          <td>...</td>
          <td>...</td>
        </tr>
        <tr>
          <th>669929</th>
          <td>Ryland Park</td>
          <td>San Jose Civic Center</td>
          <td>37.342725</td>
          <td>-121.895617</td>
        </tr>
        <tr>
          <th>669930</th>
          <td>Market at 4th</td>
          <td>Powell at Post (Union Square)</td>
          <td>37.786305</td>
          <td>-122.404966</td>
        </tr>
        <tr>
          <th>669931</th>
          <td>Market at 4th</td>
          <td>Powell at Post (Union Square)</td>
          <td>37.786305</td>
          <td>-122.404966</td>
        </tr>
        <tr>
          <th>669932</th>
          <td>South Van Ness at Market</td>
          <td>Market at Sansome</td>
          <td>37.774814</td>
          <td>-122.418954</td>
        </tr>
        <tr>
          <th>669933</th>
          <td>Market at 10th</td>
          <td>Powell Street BART</td>
          <td>37.776619</td>
          <td>-122.417385</td>
        </tr>
        <tr>
          <th>669934</th>
          <td>Grant Avenue at Columbus Avenue</td>
          <td>Howard at 2nd</td>
          <td>37.798522</td>
          <td>-122.407245</td>
        </tr>
        <tr>
          <th>669935</th>
          <td>Powell at Post (Union Square)</td>
          <td>Powell at Post (Union Square)</td>
          <td>37.788446</td>
          <td>-122.408499</td>
        </tr>
        <tr>
          <th>669936</th>
          <td>Powell at Post (Union Square)</td>
          <td>Powell at Post (Union Square)</td>
          <td>37.788446</td>
          <td>-122.408499</td>
        </tr>
        <tr>
          <th>669937</th>
          <td>Market at 4th</td>
          <td>San Francisco Caltrain (Townsend at 4th)</td>
          <td>37.786305</td>
          <td>-122.404966</td>
        </tr>
        <tr>
          <th>669938</th>
          <td>Embarcadero at Vallejo</td>
          <td>Embarcadero at Sansome</td>
          <td>37.799953</td>
          <td>-122.398525</td>
        </tr>
        <tr>
          <th>669939</th>
          <td>Market at 4th</td>
          <td>Embarcadero at Sansome</td>
          <td>37.786305</td>
          <td>-122.404966</td>
        </tr>
        <tr>
          <th>669940</th>
          <td>Market at 4th</td>
          <td>Embarcadero at Sansome</td>
          <td>37.786305</td>
          <td>-122.404966</td>
        </tr>
        <tr>
          <th>669941</th>
          <td>Davis at Jackson</td>
          <td>Davis at Jackson</td>
          <td>37.797280</td>
          <td>-122.398436</td>
        </tr>
        <tr>
          <th>669942</th>
          <td>Embarcadero at Bryant</td>
          <td>Embarcadero at Sansome</td>
          <td>37.787152</td>
          <td>-122.388013</td>
        </tr>
        <tr>
          <th>669943</th>
          <td>Market at 10th</td>
          <td>Powell Street BART</td>
          <td>37.776619</td>
          <td>-122.417385</td>
        </tr>
        <tr>
          <th>669944</th>
          <td>Post at Kearny</td>
          <td>Market at Sansome</td>
          <td>NaN</td>
          <td>NaN</td>
        </tr>
        <tr>
          <th>669945</th>
          <td>Steuart at Market</td>
          <td>Embarcadero at Sansome</td>
          <td>37.794139</td>
          <td>-122.394434</td>
        </tr>
        <tr>
          <th>669946</th>
          <td>Embarcadero at Folsom</td>
          <td>Harry Bridges Plaza (Ferry Building)</td>
          <td>37.791464</td>
          <td>-122.391034</td>
        </tr>
        <tr>
          <th>669947</th>
          <td>Mountain View City Hall</td>
          <td>Mountain View City Hall</td>
          <td>37.389218</td>
          <td>-122.081896</td>
        </tr>
        <tr>
          <th>669948</th>
          <td>Mountain View City Hall</td>
          <td>Mountain View City Hall</td>
          <td>37.389218</td>
          <td>-122.081896</td>
        </tr>
        <tr>
          <th>669949</th>
          <td>Embarcadero at Bryant</td>
          <td>Embarcadero at Folsom</td>
          <td>37.787152</td>
          <td>-122.388013</td>
        </tr>
        <tr>
          <th>669950</th>
          <td>Japantown</td>
          <td>Japantown</td>
          <td>37.348742</td>
          <td>-121.894715</td>
        </tr>
        <tr>
          <th>669951</th>
          <td>Market at 10th</td>
          <td>Market at Sansome</td>
          <td>37.776619</td>
          <td>-122.417385</td>
        </tr>
        <tr>
          <th>669952</th>
          <td>Yerba Buena Center of the Arts (3rd @ Howard)</td>
          <td>Steuart at Market</td>
          <td>37.784878</td>
          <td>-122.401014</td>
        </tr>
        <tr>
          <th>669953</th>
          <td>South Van Ness at Market</td>
          <td>Civic Center BART (7th at Market)</td>
          <td>37.774814</td>
          <td>-122.418954</td>
        </tr>
        <tr>
          <th>669954</th>
          <td>Powell Street BART</td>
          <td>Townsend at 7th</td>
          <td>37.783871</td>
          <td>-122.408433</td>
        </tr>
        <tr>
          <th>669955</th>
          <td>Harry Bridges Plaza (Ferry Building)</td>
          <td>San Francisco Caltrain (Townsend at 4th)</td>
          <td>37.795392</td>
          <td>-122.394203</td>
        </tr>
        <tr>
          <th>669956</th>
          <td>South Van Ness at Market</td>
          <td>5th at Howard</td>
          <td>37.774814</td>
          <td>-122.418954</td>
        </tr>
        <tr>
          <th>669957</th>
          <td>South Van Ness at Market</td>
          <td>5th at Howard</td>
          <td>37.774814</td>
          <td>-122.418954</td>
        </tr>
        <tr>
          <th>669958</th>
          <td>South Van Ness at Market</td>
          <td>5th at Howard</td>
          <td>37.774814</td>
          <td>-122.418954</td>
        </tr>
      </tbody>
    </table>
    <p>669959 rows × 4 columns</p>
    </div>



.. code:: python

    trips_coord2 = pd.merge(trips_coord,station_coord,how='left',left_on='end_station',right_on='name')

.. code:: python

    trips_coord2.info()


.. parsed-literal::

    <class 'pandas.core.frame.DataFrame'>
    Int64Index: 669959 entries, 0 to 669958
    Data columns (total 7 columns):
    start_station    669959 non-null object
    end_station      669959 non-null object
    start_lat        658617 non-null float64
    start_long       658617 non-null float64
    name             657435 non-null object
    lat              657435 non-null float64
    long             657435 non-null float64
    dtypes: float64(4), object(3)
    memory usage: 40.9+ MB


.. code:: python

    trips_coord2 = trips_coord2[['start_station','end_station','start_lat','start_long','lat','long']]
    trips_coord2.columns=['start_station','end_station','start_lat','start_long','end_lat','end_long']
    trips_coord2




.. raw:: html

    <div>
    <table border="1" class="dataframe">
      <thead>
        <tr style="text-align: right;">
          <th></th>
          <th>start_station</th>
          <th>end_station</th>
          <th>start_lat</th>
          <th>start_long</th>
          <th>end_lat</th>
          <th>end_long</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>0</th>
          <td>South Van Ness at Market</td>
          <td>South Van Ness at Market</td>
          <td>37.774814</td>
          <td>-122.418954</td>
          <td>37.774814</td>
          <td>-122.418954</td>
        </tr>
        <tr>
          <th>1</th>
          <td>San Jose City Hall</td>
          <td>San Jose City Hall</td>
          <td>37.337391</td>
          <td>-121.886995</td>
          <td>37.337391</td>
          <td>-121.886995</td>
        </tr>
        <tr>
          <th>2</th>
          <td>Mountain View City Hall</td>
          <td>Mountain View City Hall</td>
          <td>37.389218</td>
          <td>-122.081896</td>
          <td>37.389218</td>
          <td>-122.081896</td>
        </tr>
        <tr>
          <th>3</th>
          <td>San Jose City Hall</td>
          <td>San Jose City Hall</td>
          <td>37.337391</td>
          <td>-121.886995</td>
          <td>37.337391</td>
          <td>-121.886995</td>
        </tr>
        <tr>
          <th>4</th>
          <td>South Van Ness at Market</td>
          <td>Market at 10th</td>
          <td>37.774814</td>
          <td>-122.418954</td>
          <td>37.776619</td>
          <td>-122.417385</td>
        </tr>
        <tr>
          <th>5</th>
          <td>Golden Gate at Polk</td>
          <td>Golden Gate at Polk</td>
          <td>37.781332</td>
          <td>-122.418603</td>
          <td>37.781332</td>
          <td>-122.418603</td>
        </tr>
        <tr>
          <th>6</th>
          <td>Santa Clara at Almaden</td>
          <td>Adobe on Almaden</td>
          <td>37.333988</td>
          <td>-121.894902</td>
          <td>37.331415</td>
          <td>-121.893200</td>
        </tr>
        <tr>
          <th>7</th>
          <td>San Salvador at 1st</td>
          <td>San Salvador at 1st</td>
          <td>37.330165</td>
          <td>-121.885831</td>
          <td>37.330165</td>
          <td>-121.885831</td>
        </tr>
        <tr>
          <th>8</th>
          <td>South Van Ness at Market</td>
          <td>South Van Ness at Market</td>
          <td>37.774814</td>
          <td>-122.418954</td>
          <td>37.774814</td>
          <td>-122.418954</td>
        </tr>
        <tr>
          <th>9</th>
          <td>San Jose City Hall</td>
          <td>MLK Library</td>
          <td>37.337391</td>
          <td>-121.886995</td>
          <td>37.335885</td>
          <td>-121.885660</td>
        </tr>
        <tr>
          <th>10</th>
          <td>Spear at Folsom</td>
          <td>Embarcadero at Bryant</td>
          <td>37.790302</td>
          <td>-122.390637</td>
          <td>37.787152</td>
          <td>-122.388013</td>
        </tr>
        <tr>
          <th>11</th>
          <td>San Pedro Square</td>
          <td>Santa Clara at Almaden</td>
          <td>37.336721</td>
          <td>-121.894074</td>
          <td>37.333988</td>
          <td>-121.894902</td>
        </tr>
        <tr>
          <th>12</th>
          <td>Mountain View Caltrain Station</td>
          <td>Mountain View Caltrain Station</td>
          <td>37.394358</td>
          <td>-122.076713</td>
          <td>37.394358</td>
          <td>-122.076713</td>
        </tr>
        <tr>
          <th>13</th>
          <td>2nd at South Park</td>
          <td>2nd at South Park</td>
          <td>37.782259</td>
          <td>-122.392738</td>
          <td>37.782259</td>
          <td>-122.392738</td>
        </tr>
        <tr>
          <th>14</th>
          <td>Clay at Battery</td>
          <td>Beale at Market</td>
          <td>37.795001</td>
          <td>-122.399970</td>
          <td>37.792251</td>
          <td>-122.397086</td>
        </tr>
        <tr>
          <th>15</th>
          <td>Post at Kearney</td>
          <td>Post at Kearney</td>
          <td>37.788975</td>
          <td>-122.403452</td>
          <td>37.788975</td>
          <td>-122.403452</td>
        </tr>
        <tr>
          <th>16</th>
          <td>San Jose City Hall</td>
          <td>San Jose City Hall</td>
          <td>37.337391</td>
          <td>-121.886995</td>
          <td>37.337391</td>
          <td>-121.886995</td>
        </tr>
        <tr>
          <th>17</th>
          <td>Market at 10th</td>
          <td>Market at 10th</td>
          <td>37.776619</td>
          <td>-122.417385</td>
          <td>37.776619</td>
          <td>-122.417385</td>
        </tr>
        <tr>
          <th>18</th>
          <td>Steuart at Market</td>
          <td>Harry Bridges Plaza (Ferry Building)</td>
          <td>37.794139</td>
          <td>-122.394434</td>
          <td>37.795392</td>
          <td>-122.394203</td>
        </tr>
        <tr>
          <th>19</th>
          <td>Powell Street BART</td>
          <td>Market at 4th</td>
          <td>37.783871</td>
          <td>-122.408433</td>
          <td>37.786305</td>
          <td>-122.404966</td>
        </tr>
        <tr>
          <th>20</th>
          <td>Spear at Folsom</td>
          <td>Embarcadero at Bryant</td>
          <td>37.790302</td>
          <td>-122.390637</td>
          <td>37.787152</td>
          <td>-122.388013</td>
        </tr>
        <tr>
          <th>21</th>
          <td>Redwood City Caltrain Station</td>
          <td>Redwood City Caltrain Station</td>
          <td>37.486078</td>
          <td>-122.232089</td>
          <td>37.486078</td>
          <td>-122.232089</td>
        </tr>
        <tr>
          <th>22</th>
          <td>San Francisco City Hall</td>
          <td>San Francisco City Hall</td>
          <td>37.778650</td>
          <td>-122.418235</td>
          <td>37.778650</td>
          <td>-122.418235</td>
        </tr>
        <tr>
          <th>23</th>
          <td>Post at Kearney</td>
          <td>Market at Sansome</td>
          <td>37.788975</td>
          <td>-122.403452</td>
          <td>37.789625</td>
          <td>-122.400811</td>
        </tr>
        <tr>
          <th>24</th>
          <td>Beale at Market</td>
          <td>Steuart at Market</td>
          <td>37.792251</td>
          <td>-122.397086</td>
          <td>37.794139</td>
          <td>-122.394434</td>
        </tr>
        <tr>
          <th>25</th>
          <td>Japantown</td>
          <td>Japantown</td>
          <td>37.348742</td>
          <td>-121.894715</td>
          <td>37.348742</td>
          <td>-121.894715</td>
        </tr>
        <tr>
          <th>26</th>
          <td>Temporary Transbay Terminal (Howard at Beale)</td>
          <td>Embarcadero at Folsom</td>
          <td>37.789756</td>
          <td>-122.394643</td>
          <td>37.791464</td>
          <td>-122.391034</td>
        </tr>
        <tr>
          <th>27</th>
          <td>San Jose Civic Center</td>
          <td>San Salvador at 1st</td>
          <td>37.330698</td>
          <td>-121.888979</td>
          <td>37.330165</td>
          <td>-121.885831</td>
        </tr>
        <tr>
          <th>28</th>
          <td>South Van Ness at Market</td>
          <td>South Van Ness at Market</td>
          <td>37.774814</td>
          <td>-122.418954</td>
          <td>37.774814</td>
          <td>-122.418954</td>
        </tr>
        <tr>
          <th>29</th>
          <td>Redwood City Medical Center</td>
          <td>Broadway at Main</td>
          <td>37.487682</td>
          <td>-122.223492</td>
          <td>NaN</td>
          <td>NaN</td>
        </tr>
        <tr>
          <th>...</th>
          <td>...</td>
          <td>...</td>
          <td>...</td>
          <td>...</td>
          <td>...</td>
          <td>...</td>
        </tr>
        <tr>
          <th>669929</th>
          <td>Ryland Park</td>
          <td>San Jose Civic Center</td>
          <td>37.342725</td>
          <td>-121.895617</td>
          <td>37.330698</td>
          <td>-121.888979</td>
        </tr>
        <tr>
          <th>669930</th>
          <td>Market at 4th</td>
          <td>Powell at Post (Union Square)</td>
          <td>37.786305</td>
          <td>-122.404966</td>
          <td>37.788446</td>
          <td>-122.408499</td>
        </tr>
        <tr>
          <th>669931</th>
          <td>Market at 4th</td>
          <td>Powell at Post (Union Square)</td>
          <td>37.786305</td>
          <td>-122.404966</td>
          <td>37.788446</td>
          <td>-122.408499</td>
        </tr>
        <tr>
          <th>669932</th>
          <td>South Van Ness at Market</td>
          <td>Market at Sansome</td>
          <td>37.774814</td>
          <td>-122.418954</td>
          <td>37.789625</td>
          <td>-122.400811</td>
        </tr>
        <tr>
          <th>669933</th>
          <td>Market at 10th</td>
          <td>Powell Street BART</td>
          <td>37.776619</td>
          <td>-122.417385</td>
          <td>37.783871</td>
          <td>-122.408433</td>
        </tr>
        <tr>
          <th>669934</th>
          <td>Grant Avenue at Columbus Avenue</td>
          <td>Howard at 2nd</td>
          <td>37.798522</td>
          <td>-122.407245</td>
          <td>37.786978</td>
          <td>-122.398108</td>
        </tr>
        <tr>
          <th>669935</th>
          <td>Powell at Post (Union Square)</td>
          <td>Powell at Post (Union Square)</td>
          <td>37.788446</td>
          <td>-122.408499</td>
          <td>37.788446</td>
          <td>-122.408499</td>
        </tr>
        <tr>
          <th>669936</th>
          <td>Powell at Post (Union Square)</td>
          <td>Powell at Post (Union Square)</td>
          <td>37.788446</td>
          <td>-122.408499</td>
          <td>37.788446</td>
          <td>-122.408499</td>
        </tr>
        <tr>
          <th>669937</th>
          <td>Market at 4th</td>
          <td>San Francisco Caltrain (Townsend at 4th)</td>
          <td>37.786305</td>
          <td>-122.404966</td>
          <td>37.776617</td>
          <td>-122.395260</td>
        </tr>
        <tr>
          <th>669938</th>
          <td>Embarcadero at Vallejo</td>
          <td>Embarcadero at Sansome</td>
          <td>37.799953</td>
          <td>-122.398525</td>
          <td>37.804770</td>
          <td>-122.403234</td>
        </tr>
        <tr>
          <th>669939</th>
          <td>Market at 4th</td>
          <td>Embarcadero at Sansome</td>
          <td>37.786305</td>
          <td>-122.404966</td>
          <td>37.804770</td>
          <td>-122.403234</td>
        </tr>
        <tr>
          <th>669940</th>
          <td>Market at 4th</td>
          <td>Embarcadero at Sansome</td>
          <td>37.786305</td>
          <td>-122.404966</td>
          <td>37.804770</td>
          <td>-122.403234</td>
        </tr>
        <tr>
          <th>669941</th>
          <td>Davis at Jackson</td>
          <td>Davis at Jackson</td>
          <td>37.797280</td>
          <td>-122.398436</td>
          <td>37.797280</td>
          <td>-122.398436</td>
        </tr>
        <tr>
          <th>669942</th>
          <td>Embarcadero at Bryant</td>
          <td>Embarcadero at Sansome</td>
          <td>37.787152</td>
          <td>-122.388013</td>
          <td>37.804770</td>
          <td>-122.403234</td>
        </tr>
        <tr>
          <th>669943</th>
          <td>Market at 10th</td>
          <td>Powell Street BART</td>
          <td>37.776619</td>
          <td>-122.417385</td>
          <td>37.783871</td>
          <td>-122.408433</td>
        </tr>
        <tr>
          <th>669944</th>
          <td>Post at Kearny</td>
          <td>Market at Sansome</td>
          <td>NaN</td>
          <td>NaN</td>
          <td>37.789625</td>
          <td>-122.400811</td>
        </tr>
        <tr>
          <th>669945</th>
          <td>Steuart at Market</td>
          <td>Embarcadero at Sansome</td>
          <td>37.794139</td>
          <td>-122.394434</td>
          <td>37.804770</td>
          <td>-122.403234</td>
        </tr>
        <tr>
          <th>669946</th>
          <td>Embarcadero at Folsom</td>
          <td>Harry Bridges Plaza (Ferry Building)</td>
          <td>37.791464</td>
          <td>-122.391034</td>
          <td>37.795392</td>
          <td>-122.394203</td>
        </tr>
        <tr>
          <th>669947</th>
          <td>Mountain View City Hall</td>
          <td>Mountain View City Hall</td>
          <td>37.389218</td>
          <td>-122.081896</td>
          <td>37.389218</td>
          <td>-122.081896</td>
        </tr>
        <tr>
          <th>669948</th>
          <td>Mountain View City Hall</td>
          <td>Mountain View City Hall</td>
          <td>37.389218</td>
          <td>-122.081896</td>
          <td>37.389218</td>
          <td>-122.081896</td>
        </tr>
        <tr>
          <th>669949</th>
          <td>Embarcadero at Bryant</td>
          <td>Embarcadero at Folsom</td>
          <td>37.787152</td>
          <td>-122.388013</td>
          <td>37.791464</td>
          <td>-122.391034</td>
        </tr>
        <tr>
          <th>669950</th>
          <td>Japantown</td>
          <td>Japantown</td>
          <td>37.348742</td>
          <td>-121.894715</td>
          <td>37.348742</td>
          <td>-121.894715</td>
        </tr>
        <tr>
          <th>669951</th>
          <td>Market at 10th</td>
          <td>Market at Sansome</td>
          <td>37.776619</td>
          <td>-122.417385</td>
          <td>37.789625</td>
          <td>-122.400811</td>
        </tr>
        <tr>
          <th>669952</th>
          <td>Yerba Buena Center of the Arts (3rd @ Howard)</td>
          <td>Steuart at Market</td>
          <td>37.784878</td>
          <td>-122.401014</td>
          <td>37.794139</td>
          <td>-122.394434</td>
        </tr>
        <tr>
          <th>669953</th>
          <td>South Van Ness at Market</td>
          <td>Civic Center BART (7th at Market)</td>
          <td>37.774814</td>
          <td>-122.418954</td>
          <td>37.781039</td>
          <td>-122.411748</td>
        </tr>
        <tr>
          <th>669954</th>
          <td>Powell Street BART</td>
          <td>Townsend at 7th</td>
          <td>37.783871</td>
          <td>-122.408433</td>
          <td>37.771058</td>
          <td>-122.402717</td>
        </tr>
        <tr>
          <th>669955</th>
          <td>Harry Bridges Plaza (Ferry Building)</td>
          <td>San Francisco Caltrain (Townsend at 4th)</td>
          <td>37.795392</td>
          <td>-122.394203</td>
          <td>37.776617</td>
          <td>-122.395260</td>
        </tr>
        <tr>
          <th>669956</th>
          <td>South Van Ness at Market</td>
          <td>5th at Howard</td>
          <td>37.774814</td>
          <td>-122.418954</td>
          <td>37.781752</td>
          <td>-122.405127</td>
        </tr>
        <tr>
          <th>669957</th>
          <td>South Van Ness at Market</td>
          <td>5th at Howard</td>
          <td>37.774814</td>
          <td>-122.418954</td>
          <td>37.781752</td>
          <td>-122.405127</td>
        </tr>
        <tr>
          <th>669958</th>
          <td>South Van Ness at Market</td>
          <td>5th at Howard</td>
          <td>37.774814</td>
          <td>-122.418954</td>
          <td>37.781752</td>
          <td>-122.405127</td>
        </tr>
      </tbody>
    </table>
    <p>669959 rows × 6 columns</p>
    </div>



.. code:: python

    a = trips_coord2.loc[trips_coord.start_station != trips_coord.end_station,:].head()

.. code:: python

    x = []
    y = []
    fin = []
    x.append(a.ix[10,'start_lat'])
    x.append(a.ix[10,'start_long'])
    fin.append(tuple(x))
    y.append(a.ix[10,'end_lat'])
    y.append(a.ix[10,'end_long'])
    fin.append(tuple(y))
    h = gmaps.Map()
    directions_layer = gmaps.Directions(data=fin)
    h.add_layer(directions_layer)
    h

