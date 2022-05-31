# Preparation of traffic data set

* Add one extra feature like Speed limit to Travel-sensors dataset which specifies the allowed speed limit defined by the City of Austin [5].
* Merge the following two datasets Radar-Traffic-counts and Travel- sensors using a left join and Kits Id as the field of the relationship between the two datasets.
* Add a target called Validity to this new merged dataset, which is assigned by comparing every registered speed with speed limit. If the speed is greater than the speed limit then validity value is 0, otherwise is 1.
* Identify features without values and remove columns in this new
traffic dataset. The following features were removed:
    - Corridor name
    - County
    - Cross St Aka
    - Cross St Segment Id
    - Jurisdiction
    - Landmark
    - Location Latitude
    - Location Longitude
    - Primary St Aka
    - Primary St Segment Id
    - Reader Id
* Identify duplicate features and remove them. The only duplicated
feature was ‘Kits Id1’.
* Find the features which have a constant value and remove them
since they won’t provide any useful information to our predictive model.

<center>
<br>
Table 4. Features with constant values

*Variable* |  *Value*  
--------|--------
Atd Location Id | LOC17-010435
Location Type | ROADWAY
Primary St Block | 2800
Cross St Block | 2801
Turn On Date | 05/05/2013 05:00:00 AM +0000
Source DB ID | 595a74203048bf4b5388ba58
Signal Eng Area | SOUTHWEST
Sensor Type | RADAR
Sensor Status | TURNED_ON
Sensor Mfg | Wavetronix
Primary St Segment Display Name | S LAMAR BLVD (2023812)
Primary St | LAMAR BLVD
Modified Date | 07/03/2017 04:43:00 PM +0000
Location Name | LAMAR BLVD / MENCHACA RD
Atd Sensor Id | 160
Location | POINT (-97.781705 30.243875)
Kits Id | 1
Jurisdiction Label | AUSTIN FULL PURPOSE
Ip Comm Status | ONLINE
Intersection Name | LAMARMENCHACA
Cross St Segment Display Name | MENCHACA RD (2023827)
Cross St | MENCHACA RD
Council District | 5
Comm Status Datetime Utc | 03/04/2021 09:35:00 AM +0000
Coa Intersection Id | 5152101
Speed Limit | 40
</center>

* Remove ‘Time Bin’ column since it has an older date value lower than July 2017 which is 12/30/1899.
* Convert ‘Read Date ’column that contains Date objects to DateTime64 type. Then divide each column in four different columns that contain the year, month, day, hour and minute of Read Date and remove original column.

<center>
<br>
Table 5. Original feature Read Date and their new generated features

*Original Feature* |  *New Features*  
--------|--------
Read Date | Read Date Year <br> Read Date Month <br> Read Date Day <br> Read Date Hour <br> Read Date Minute
</center>

* Remove ‘Row ID’ columns since this is a unique identifier that doesn’t provide useful information to our model.
* Identify and convert categorical features to numerical values. The following are the categorical features and their new generated features.

<center>
<br>
Table 6. Categorical features and their equivalent numeric features

*Original Feature* |  *New Features*  
--------|--------
Direction | Direction_NB <br> Direction_SB
Lane | Lane_NB_in <br> Lane_NB_out <br> Lane_SB_in <br> Lane_SB_out

</center>

* Perform feature selection to find the best 5 features to contribute our predictive model. Since our problem has numerical inputs and categorical output, we chose ANOVA correlation coefficient technique for performing feature selection. Keep these features and remove the rest of them. The selected features are as follows:
    - Year 
    - Hour
    - Occupancy 
    - Speed
    - Volume
