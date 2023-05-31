# swag



| makeresults 
| eval startTime=strptime("2023-05-24 00:00:00", "%Y-%m-%d %H:%M:%S")
| eval endTime=strptime("2023-05-24 23:59:59", "%Y-%m-%d %H:%M:%S")
| foreach [eval hour=startTime; hour<=endTime; hour+=3600] 
    [ search index=apigee RequestVerb=POST earliest=@hour+3600 latest=@hour+7200 
    | stats count by UserIP 
    | sort -count 
    | head 10
    | eval hour=strftime(hour, "%Y-%m-%d %H:%M:%S")
    | eval report="Hour: " . hour . "\n" . "Top 10 User IPs:\n" . "UserIP: " . UserIP . ", Count: " . count
    | table report ]
