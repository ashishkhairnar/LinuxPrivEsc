1) **Sticky bits -**

    **Look for sticky bits in the file system - SUID/GUID**
     <br />
     - find / -perm -u=s -type f 2>/dev/null <br />
     > ls -l /bin/su <br />
     > rw**s**r-xr-x 1 root root 40128 May 17  2012 /bin/su <br />
     > above indicates "s" or SUID bit is set.<br />


2) **Checking Process running every now and then if any.**

     Credit: @ippsec Nineveh Video on YouTube
     
    > #!/bin/bash <br />
    > IFS=$'\n' <br />
    > old_process=$(ps -eo command) <br />
    > while true; do <br />
    > 	new_process=$(ps -eo command) <br />
    > 	diff <(echo "$old_process") <(echo "$new_process") <br />
    > 	sleep 1 <br />
    > 	old_process=$new_process <br />
    > done  <br />
