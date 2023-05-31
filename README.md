# swag



| bin _time span=1h
| stats count by userip, _time
| eventstats rank(count) as rank by _time
| where rank <= 10
| timechart span=1h limit=10 sum(count) as TotalCount by userip
