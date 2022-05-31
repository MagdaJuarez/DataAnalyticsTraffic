# **Data Analytics of Traffic Data Set**
<p>
Repository of data science experiments of traffic data set in intersection La Mar Boulevard - Menchaca, Austin Texas, USA.
</p>

## **1. Question**
<p>
Is it possible to predict trends of traffic speed at the intersection of La Mar Boulevard and Menchaca, Austin Texas, USA?
</p>

## **2. Data explanation**
<p>
The traffic dataset comprises hourly readings from Wavetronix radar sensors located in junction La Mar with Menchaca, Austin, Texas. A data frame with 437,900 rows over four years from July 2017 to September 2021. It contains 54 numerical and categorical variables whose names and descriptions are shown in [1, Tab. 1] and the data sample is depicted in Table 2 and Table 3.
<br>This dataset comprises the join of two dataset one which is Radar_Traffic_Counts.csv and the other Travel_sensors.csv, after that it was filtered by intersection name LaMar_Menchaca to get only the data from this intersection.

<br>According to the City of Austin Transportation Department[2], the Radar Traffic counts dataset “... contains information about travel sensors in Austin, TX. Travel sensors are owned and operated by the City of Austin Transportation Department and are used to monitor traffic conditions across the city.” Also, the Travel Sensors dataset, according to City of Austin Transportation Department [2] contains information about travel sensors in Austin, TX.
<br>This dataset contains readings from Wavetronix travel sensors which are radar and bluetooth. It’s public to access, use and according to the City of Austin Open Terms of Use[3] this dataset is under a public domain and it could be used as long as a proper credit is given. It doesn’t contain sensitive data and values are not encrypted.

<br>Both datasets were stored in a csv file and published in the Data.gov website [1] and the sensors have not lowered and compressed the data.
<br>The traffic dataset represents something positive as reported by the Arterial Management Division [4] which uses this data to monitor traffic patterns and adjust signal timing in response to traffic needs.
It contains archive data, which was created on November 6th, 2017, updated on December 18th, 2021 and published on April 19th, 2021.
</p>

<center>
Table 1. Name, description, type of variables and categories for traffic data set

*#* |  *Variable name*  |  *Description*   |   *Type*  |  *Example*  |  *Category*   |   *Quantity* |  *Range*
--------|--------|------|------|-----|-------------|--------|-------
1 | Row ID|	An unique ID for each row  |   String|	a3308da32f776464fb31959036020eff|	Nominal	| |	Infinite list
2 | Detector ID |	 A unique number given to each|   Integer|	43|		|Continuous|	From 1 to 102
3 | KITS ID	 |   The ID of the wavetronix travel sensor in KITS, the city's Advanced Traffic Management System.|   Integer|	14| 	|Continuous|	From 1 to 26
4 | Read Date	 |   The date the data was collected by the radar device.|   Date|	01/24/2018 05:45:00 AM +0000|	|Continuous|	Finite range
5 | Intersection Name | The general location of the sensor. | String | Rober E LeeBarton Srpings | Nominal |  | Short finite list
6 | Lane | The lane that was counted by the device. First two characters indicates direction, NB = Northbound. The last characters explain which lane in that direction. "in" is inside lane, or the lane closest to the center of the road in the direction of travel. | String | NB_in | Nominal |  | Finite list
7 | Volume| The volume, or number of vehicles detected by the sensor, in the last 15 minutes. | Integer | 1 |  | Continuous | From 0 to 255
8 | Occupancy | According to Shanmukha *6*, occupancy is the ratio of the sum of the lengths of the vehicles to the length of the road section in which those vehicles are present. | Integer | 0 |  | Continuous | From 0 to 100
9 | Speed | The average speed of the vehicles that passed by the sensor in the last 15 minutes.  | Integer | 24 |  | Continuous | From 0 to 149
10 | Month | The numeric month of the data. | Integer | 1 |  | Continuous | From 1 to 12
11 | Day | The numeric day of the data. | Integer | 23 |  | Continuous | From 1 to 31
12 | Year | The numeric year of the data | Integer | 2018 |  | Continuous | From 2017 to 2021
13 | Hour | The numeric hour of the data. | Integer | 23 |  | Continuous | From 0 to 23
14 | Minute | The numeric minute of the data. | Integer | 45 |  | Continuous | From 0 to 59
15 | Day of Week | Starting with Sunday is 0 and Monday is 1, and so on. | Integer | 2 |  | Continuous | From 0 to 6
16 | Time Bin | Formatted hour based on Hour and minute columns. | String | 23:45 | Nominal |  | Finite list
17 | Direction | The direction of travel. This information is extracted from the Lane column. | String | NB | Nominal |  | Finite list
18 | Reader Id | Sensor reader ID | String |  | Nominal |  | Values not found
19 | Atd Sensor Id |  | Integer | 153 |  | Discrete | Finite list
20 | Kits Id1 | The ID of the radar sensors in the KITS database. | Integer | 14 |  |  | Finite list
21 | Atd Location Id |  | String | LOC16-007265 |  |  | Finite list
22 | Modified Date | The date sensor was updated | Date | 07/03/2017 03:28:00 PM +0000 |  | Continuous | Finite range
23 | Sensor Status | The sensor status | String | TURNED_ON | Nominal |  | Short finite list
24 | Turn On Date  | The date sensor was turned on | Date | 05/05/2015 05:00:00 AM +0000 |  | Continuous | Finite range
25 | Sensor Type | The sensor type | String | RADAR | Nominal |  | Short finite list
26 | Sensor Mfg |  | String | Wavetronix |  Nominal |  | Short finite list
27 | Coa Intersection Id |  | Integer |  |  | Discrete | Finite list
28 | Primary St Segment Id | Primary Street Segment ID | String |  | Nominal |  | Values not found
29 | Cross St Segment Id | Cross street segment ID | String |  | Nominal |  | Values not found
30 | Landmark | Landmark | String |  | Nominal |  | Values not found
31 | Primary St Aka | Known name of primary street | String |  | Nominal |  | Values not found
32 | Cross St Aka | Know name of cross street | String |  | Nominal |  | Values not found
33 | Signal Eng Area |  | String | SOUTHWEST | Nominal |  | Short finite list
34 | Council District | Council district ID | Integer | 5 |  | Discrete | Finite list
35 | Jurisdiction |  | String |  | Nominal |  | Values not found
36 | Location Type | Type of location | String | ROADWAY | Nominal |  | Short finite list
37 | Location Name | Name of location | String | 400 BLK AZIE MORTON RD (South of Barton Springs Rd) | Nominal |  | Finite list
38 | Primary St | Name of primary street | String | AZIE MORTON RD | Nominal |  | Finite list
39 | Cross St | Name of cross street | String |  | Nominal |  | Finite list
40 | Primary St Block | Block number of primary street | Integer | 400 |  | Discrete | Finite range
41 | County | Id of County | String |  |  | Values not found
42 | Cross St Block | Block number of cross street | Integer |  |  | Discrete | Finite range
43 | Ip Comm Status | The IP communication status of the device |  String | OFFLINE | Nominal |  | Short finite list
44 | Comm Status Datetime Utc | The UTC date/time at which the comm status was updated. | Date | 10/22/2021 08:35:00 AM +0000 |  | Continuous | Finite range
45 | Location Latitude | Location longitude of the sensor | String |  | Nominal |  | Values not found
46 | Location Longitude | Location latitude of the String sensor | String |  | Nominal |  | Values not found
47 | Source DB ID | The sensor's unique identifier in the asset management system database. | String | 595a62bb660ba54ca7f6eb03 | Nominal |  | Finite list
48 | Location |  Location latitude and longitude of the sensor | String | POINT (-97.765802 30.264245) | Nominal |  | Finite list
49 | Primary St Segment Display Name | Name of primary street segment | String | AZIE MORTON RD (2041226) | Nominal |  | Finite list
50 | Cross St Segment Display Name | Name of cross street segment | String |  | Nominal |  | Finite list
51 | Jurisdiction Label | The name of the jurisdiction | String | AUSTIN FULL PURPOSE | Nominal |  | Short finite list
52 | Corridor Name | The name of the intersection | String |  | Nominal |  | Values not found
53 | Speed Limit | The speed limit defines by Texas Department of Public Safety. | Integer |  | 40 |  | Continuous | Finite range
54 | Speed Validity | Determines if a speed exceeds the speed limit | Integer |  | 1 |  | Discrete | Short finite list


<br>
Table 2. Representative sample of data where It can be seen missing and wrong values

Row Id |  *Detector*  |  *Kits Id*   |   *Read Date*  |  *Intersection Name*  |  *Lane*   |   *Volume* |  *Occupancy* | *Speed* | *Month* | *Day* | *Year* | *Hour* | *Minute* | *Day of Week* | *Time Bin* | *Direction*
--------|--------|------|------|-----|-------------|--------|-------|--------|--------|------|------|-----|-------------|--------|-------|-------
17e8c8848df83e21cee36315871b980f| 43 | 14 | 01/24/2018 05:45:00 AM +0000 | Robert E LeeBarton Springs | NB | 1 | 0 | 24 | 1 | 23 | 2018 | 23 | 45 | 2 | 23:45 | NB
8deb5fed08a66e215b962d76fe3e3fec | 74 | 19 | 01/24/2018 05:45:00 AM +0000 | KINNEY LAMAR | Lane1 | 1 | 0 | 9 | 1 | 23 | 2018 | 23 | 45 | 2 | 23:45 | None
081206{ “error”: true  “message”:“Internal error”  “status”: 500 } | ? | ? | ? | ? | ? | ? | ? | ? | ? | ? | ? | ? | ? | ? | ? |  
246c87f5115a2d1ebcce13e5c174b669 | 3 | 1 | 01/19/1970 03:55:37 AM +0000 | LAMARMANCHACA | SB_in | 100 | 6 | 34 | 9 | 24 | 2019 | 10 | 0 | 2 | 10:00 | SB

</center>

## **3. Data composition**
We could see some important features about dataset composition as follows:
* Traffic dataset comprises some variable data types as seen in Table 2. Examples, types and variables of this dataset are
shown in Table 1.
* It includes raw data and neither function nor algorithm was used to store the data.
* It includes additional metadata as follows:
    - Sensor details: Turn on date, Modified date, type of sensor, location, ip communication status, communication status datetime.
    - Sensor location details: Location type, name, primary street, cross street, cross street block, location point, corridor name.
* The data is observational and is quite accurate since there are only missing values when the sensor was not able to connect with the server as seen in Table 2.
* The last version of this dataset is 1.1 and was last updated on October 18th, 2021.

## **4. Methodology**
### **4.1. [Preparation of traffic data set](/PreparationDataSet.md)**
### **4.2. [Exploratory analysis](/ExploratoryAnalysis.md)**
### **4.3. [Development of predictive model](/DevelopmentModel.md)**
## **5. [Results](/Results.md)**
## **6. [References](/References.md)**
