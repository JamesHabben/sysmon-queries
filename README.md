# sysmon-queries
Queries to parse sysmon event log file with Microsoft logparser.<br>
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

# Sample Queries
###process-create-terminate
Query to combine the records which are process start(1) and process terminate(5).

###process-start-stop-by-user
Query to display all processes started(1) by a specified user logon. Also in the results are terminate records(5) that have matching PID to a process matching the user logon. There will be extra terminate records(5) since there are no logons associated with it, but the first terminate(5) should be the matching record for the displayed start record(5). <br>
<img src="https://github.com/JamesHabben/sysmon-queries/blob/master/images/process-start-stop-by-user.PNG" width=250/>

###file-create-time
Query to display all file create date change records(2).

###file-create-time-backwards
Query to display all date records(2) that have a new date that is older than the previous date. Essential, detection of actions consistent with timestomp/filetouch/setmace activity. This query excludes records that have 'chrome.exe' in the ImagePath property because Google Chrome makes a ton of date changes for some reason. I also found ExFil type artifacts from files I was copying to an external USB drive. <br>
<img src="https://github.com/JamesHabben/sysmon-queries/blob/master/images/file-create-timestomp.PNG" width=250 />

###file-create-program-count
Query to get a unique list of programs that have made date changes(2) to some file somewhere. Plus a column to count the number of changes that have been made. <br>
<img src="https://github.com/JamesHabben/sysmon-queries/blob/master/images/file-create-program-count.PNG" width=250 />

###file-create-file-count
Query to get a unique list of files that have had their date changed(2) and the program that made the change. Plus a count of the number of times that file's date has been changed.

###file-create-file-count-no-chrome
Same as file-create-file-count only this removes any records made by 'chrome.exe' since it makes a huge number of changes.

###driver-load
Query to display all driver load records(6)

###image-load
Query to display all image load records(7)

###image-load-wininet-winsock32
Query to display all records for processes that have image loads(7) pointing at wininet.dll or winsock32.dll. <br>
<img src="https://github.com/JamesHabben/sysmon-queries/blob/master/images/imageload-wininet-winsock32.PNG" width=250 />

###network-connection
Query to display all records for network connections(4).

###network-socket-count
Query to display a unique list of network sockets (IP and port) from the connection records(4). Plus a count of the number of records for each socket.

###network-connection-count
Query to display unique list of network connections from the connection records(4). Plus a count of the number of records for each connection.
