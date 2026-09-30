# Data

The raw crash dataset is intentionally **not stored in the current repository tree**.

The notebooks expect the input file at:

```text
data/crash_data.csv
```

## Source

The analysis is based on Montgomery County, Maryland crash data. The official open-data source for the driver-level dataset is:

https://data.montgomerycountymd.gov/Public-Safety/Crash-Reporting-Drivers-Data/mmzv-x632

The portal is updated over time, so a newly downloaded dataset may not reproduce the historical notebook outputs exactly.

The original repository snapshot used by this project was stored as `crash_data.csv` and had Git blob SHA:

```text
261a4301ce786d476d501ff6d4badc5c3791b7ba
```

That historical blob remains available through the repository history even though the large CSV is removed from the current tree.
