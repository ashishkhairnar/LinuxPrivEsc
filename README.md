1) **Sticky bits -**
------------------------
Look for sticky bits in the file system - SUID/GUID
   - find / -perm -u=s -type f 2>/dev/null <br />
     > ls -l /bin/su <br />
     > rw**s**r-xr-x 1 root root 40128 May 17  2012 /bin/su <br />
     > above indicates "s" or SUID bit is set.<br />


2) **Checking Process running every now and then if any. Credit: @ippsec Nineveh Video**
------------------------------------------------------------------------------------------------

#!/bin/bash
IFS=$'\n'
old_process=$(ps -eo command)
while true; do
	new_process=$(ps -eo command)
	diff <(echo "$old_process") <(echo "$new_process")
	sleep 1
	old_process=$new_process
done
