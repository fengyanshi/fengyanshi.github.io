Ship-wakes
*************

|  Specify a folder which contains a number of vessel files, vessel_00001, vessel_00002, ...
|   VESSEL_FOLDER = ./

| Specify the number of vessels (e.g., 5)
|   NumVessel = 5
|
|   In vessel_00001, for example, provide vessel name, vessel length, width, shape parameters, draft and time series of vessel path:  
|   Title: Vessel # 1 
|   Blue_Star_I
|   Length(m), Width(m), Alpha(m), Beta(m), P(unit)
|   20.0  10.0, 0.5, 0.5, 1.0
|   0.0000000e+00,   5.6000000e+02,   5.0000000e+02
|   1.0000000e+00,   5.6374897e+02,   5.0255132e+02
|   ...  
| In the time series, the first column is time in seconds, the second and the third are x and y in meters, respectively. 
