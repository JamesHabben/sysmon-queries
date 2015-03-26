# sysmon-queries
Queries to parse sysmon event log file with Microsoft logparser.
https://technet.microsoft.com/en-us/sysinternals/dn798348

# Sysmon Event Format
Sysmon creates event log entries in the Windows event log viewer, but the details are not seen from the list view.<br>
<img src="https://github.com/JamesHabben/sysmon-queries/blob/master/images/event-list.PNG" width=600 />

The details can been seen in the individual event details, but it is hard to filter on details of the Sysmon data.<br>
<img src="https://github.com/JamesHabben/sysmon-queries/blob/master/images/event-details.PNG" width=300 />

# Usage
These queries allow the use of the logparser tool to extract the individual values from inside the sysmon data field. This will export the results to a variety of formats for further analysis.<br>
http://www.microsoft.com/en-us/download/details.aspx?id=24659<br>
<img src="https://github.com/JamesHabben/sysmon-queries/blob/master/images/log-parser-cmd.PNG" width=300/>

They can also be used with log parser lizard to view the data in the GUI<br>
http://lizard-labs.com/log_parser_lizard.aspx<br>
<img src="https://github.com/JamesHabben/sysmon-queries/blob/master/images/log-lizard-processes.PNG" width=600 />

I created different queries because the fields are different between the different event IDs generated.
