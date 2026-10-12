# Daily Pandas and Matplotlib Practice with ChatGPT, Claude, Meta AI (WhatsApp) 12th October 2026
<b>GIS weather - station dataset:</b></br>
Start with this:</br>
```Python
import pandas as pd

stations = pd.DataFrame({
    "site_id": [101, 102, 103, 104, 105, 106],
    "state": ["WB", "WB", "AS", "AS", "OD", "OD"],
    "landuse": ["Urban", "Forest", "Forest", "Urban", "Urban", "Forest"],
    "rainfall": [400, 200, 600, 300, 500, 700]
})

ndvi_data = pd.DataFrame({
    "site_id": [101, 102, 103, 104, 105, 106],
    "ndvi": [0.25, 0.75, 0.85, 0.30, 0.40, 0.80]
})
```
<b>Task 1 - </b>```merge()```</br>
Merge ```ndvi_data``` into ```stations```, matching the rows using ```site_id```.</br>
Store the merged result back in ```stations```</br>

<b>Task 2 - </b>```transform()```</br>
Add a new column called ```state_mean_rainfall```</br>
It should contain the mean rainfall of each station's state, while <b>preserving all six rows</b></br>

<b>Task 3 - </b>```pivot_table()```</br>
Create a new Dataframe called ```rainfall_pivot``` with:</br>

<ul>
  <li> index -> state
  <li> columns -> landuse
  <li> values -> rainfall
  <li> aggfunc -> "mean"
</ul>

# Script
Pandas & Matplotlib script:</br>
```Python
#%%
import pandas as pd
import matplotlib
matplotlib.use("module://matplotlib_inline.backend_inline")
import matplotlib.pyplot as plt
stations = pd.DataFrame({
    "site_id": [101, 102, 103, 104, 105, 106],
    "state": ["WB", "WB", "AS", "AS", "OD", "OD"],
    "landuse": ["Urban", "Forest", "Forest", "Urban", "Urban", "Forest"],
    "rainfall": [400, 200, 600, 300, 500, 700]
})
ndvi_data = pd.DataFrame({
    "site_id": [101, 102, 103, 104, 105, 106],
    "ndvi": [0.25, 0.75, 0.85, 0.30, 0.40, 0.80]
})
stations = stations.merge(ndvi_data)
stations["station_mean_rainfall"] = stations.groupby("state")["rainfall"].transform("mean")
stations_p_t = stations.pivot_table(index="state",
                                    columns="landuse",
                                    aggfunc="mean",
                                    values="rainfall").reset_index()
print()
print("The Dataframe of the Station:")
print(stations)
print()
print("The Pivot Table of the Station:")
print(stations_p_t)
print()
plt.title("The Histogram Plotting")
plt.xlabel("")
plt.ylabel("")
plt.style.use("dark_background")
plt.bar(stations["station_mean_rainfall"].index,stations["station_mean_rainfall"].values)
plt.show()
```
# Solution
<b>Pandas output:</b></br>
```
The Dataframe of the Station:
   site_id state landuse  rainfall  ndvi  station_mean_rainfall
0      101    WB   Urban       400  0.25                  300.0
1      102    WB  Forest       200  0.75                  300.0
2      103    AS  Forest       600  0.85                  450.0
3      104    AS   Urban       300  0.30                  450.0
4      105    OD   Urban       500  0.40                  600.0
5      106    OD  Forest       700  0.80                  600.0

The Pivot Table of the Station:
landuse state  Forest  Urban
0          AS   600.0  300.0
1          OD   700.0  500.0
2          WB   200.0  400.0
```
<b>Matplotlib output:</b></br>
<img width="918" height="697" alt="image" src="https://github.com/user-attachments/assets/9133d591-2404-4886-8ddc-baf881280673" />
