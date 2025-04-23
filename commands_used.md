# 💻 Commands Used – Day #19: Splunk User Creation Lab

## Q1: Count How Many Users Were Created
```spl
| inputlookup auditd_logs 
| stats dc(uid) as user_creation_count
```

## Q2: Identify Who Changed david_wilson's Password
```spl
| inputlookup auditd_logs 
| search path="/etc/shadow" uid=1015 process="nano"
| table _time uid process path
```

## Q3: Confirm UID of david_wilson
```spl
| inputlookup auditd_logs 
| search path="/etc/shadow" uid=1015
| table _time uid process path
