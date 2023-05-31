# swag



| bin _time span=1h
| stats count by userip, _time
| streamstats sum(count) as TotalCount by _time
| top 10 TotalCount by _time
