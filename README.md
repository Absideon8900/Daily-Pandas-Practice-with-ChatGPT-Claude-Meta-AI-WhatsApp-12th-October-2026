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

# Solution
Pandas & Matplotlib script:</br>

