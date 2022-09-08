# apc-dash-pro
Dashboard for grafana with InfluxDB and telegraf

Link to Grafana dashboard [link](https://grafana.com/grafana/dashboards/16874-apc-ups-dashboard/) and id is `16874`.

I couldn’t find a dashboard that suited my needs, so I made my own. Queries could likely be improved upon, but seem to be fine in my case.
Displays all the data available from apcupsd plugin from telegraf, after importing check and update variables.

`TimeZone` = Time zone in UTC AvgKWprice = Price per KW/h InfluxBucket = Your buck where Telegraf saves data
`UpsPower` = Your UPS power rating in watts UpsName = Name of your ups in bucket, telegraf tries to find them automatically
`InfluxBucket` = Original bucket
`InfluxBucket_ds` = Downsampled bucket
`Downsample_len` = Retention time of `InfluxBucket`

Features:
- Dynamicly displays data from downsampled and original bucket
- Finds all UPS's in bucket
- Timezones, to correct for `window()` offset
- Data displayed:
  - Monthly power usage (smoothed, daily) + prediction, cost
  - Daily power usage (smoother, hourly) + prediction, cost
  - Live power usage
  - In and Out AC voltage
  - Battery voltage and temperature
