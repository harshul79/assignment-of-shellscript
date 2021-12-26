# assignment-of-shellscript
all assignment of linux
Exercise_1 - Write a shell script that prints “Shell Scripting is Fun!” on the screen
#!/bin/bash
echo “Shell Scripting is Fun!”
Output
[svimukthi@sanka Shell_Scripting]$ ./exe1.sh
Shell Scripting is Fun!
Exercise_2 - Modify the shell script from exercise 1 to include a variable. The variable will hold the contents of the message “Shell Scripting is Fun!”
#!/bin/bash
NAME=”Shell Scripting is Fun!”
echo $NAME
Output
[svimukthi@sanka Shell_Scripting]$ ./exe2.sh
Shell Scripting is Fun!
Exercise_3 - Store the output of the command “hostname” in a variable. Display “This script is running on _.” where “_” is the output of the “hostname” command.
#!/bin/bash
HOSTNAME=$(hostname)
echo “This script is running on $HOSTNAME”
Output
[svimukthi@sanka Shell_Scripting]$ ./exe3.sh
This script is running on vimukthi
Exercise_4 - Write a shell script to check to see if the file “file_path” exists. If it does exist, display “file_path passwords are enabled.” Next, check to see if you can write to the file. If you can, display “You have permissions to edit “file_path.””If you cannot, display “You do NOT have permissions to edit “file_path””
#!/bin/bash
FILE=”/home/svimukthi/Assignment/sanka”
if [ -e “$FILE” ]
  then
     echo “$FILE passwords are enabled”
fi
if [ -x “$FILE” ]
  then
    echo “You have permition to execute $FILE”
  else
    echo “You do Not have permissions to execute $FILE”
fi
Output
[svimukthi@sanka Shell_Scripting]$ ./exe4.sh
/home/svimukthi/Assignment/sanka passwords are enabled
You have permition to execute /home/svimukthi/Assignment/sanka
Exercise_5 - Write a shell script that displays “man”,”bear”,”pig”,”dog”,”cat”,and “sheep” on the screen with each appearing on a separate line. Try to do this in as few lines as possible.
#!/bin/bash
ANIMALS=”man bear pig dog cat sheep”
for ANIMAL in $ANIMALS
  do
    echo $ANIMAL
  done
Output
[svimukthi@sanka Shell_Scripting]$ ./exe5.sh
man
bear
pig
dog
cat
sheep
Exercise_6 - write a shell script that prompts the user for a name of a file or directory and reports if it is a regular file, a directory, or another type of file. Also perform an ls command against the file or directory with the long listing option.
#!/bin/bash
echo “Enter the file path”
read FILE
if [ -f “$FILE” ]
  then
    echo “$FILE is a reguler file”
elif [ -d “$FILE” ]
  then
    echo “$FILE is a directory”
else
    echo “$FILE is another type of file”
fi
ls -l $FILE
Output
[svimukthi@sanka Shell_Scripting]$ ./exe6.sh
Enter the file path
/home/svimukthi/sanka
/home/svimukthi/sanka is a directory
total 4
drwxr-xr-x. 2 svimukthi svimukthi 30 Nov 13 20:18 hs
-rw-rw-r — . 1 svimukthi svimukthi 12 Nov 12 12:09 sanka.txt
d — x — — — . 2 svimukthi svimukthi 20 Dec 13 18:53 test
Exercise_7 - Modify the previous script to that it accepts the file or directory name as an argument instead of prompting the user to enter it.
#!/bin/bash
FILE=$1
if [ -f “$FILE” ]
  then
    echo “$FILE is a reguler file”
elif [ -d “$FILE” ]
  then
    echo “$FILE is a directory”
else
   echo “$FILE is another type of file”
fi
ls -l $FILE
Output
[svimukthi@sanka Shell_Scripting]$ ./exe7.sh /home/svimukthi/sanka
/home/svimukthi/sanka is a directory
total 4
drwxr-xr-x. 2 svimukthi svimukthi 30 Nov 13 20:18 hs
-rw-rw-r — . 1 svimukthi svimukthi 12 Nov 12 12:09 sanka.txt
d — x — — — . 2 svimukthi svimukthi 20 Dec 13 18:53 test
Exercise_8 - Modify the previous script to accept an unlimited number of files and directories as arguments.
#!/bin/bash
FILES=$@
for FILE in $FILES
  do
    if [ -f “$FILE” ]
      then
         echo “$FILE is a reguler file”
    elif [ -d “$FILE” ]
      then
         echo “$FILE is a directory”
    else
         echo “$FILE is another type of file”
    fi
   ls -l $FILE
  done
Output
[svimukthi@sanka Shell_Scripting]$ ./exe8.sh /home/svimukthi/sanka /hms/apps
/home/svimukthi/sanka is a directory
total 4
drwxr-xr-x. 2 svimukthi svimukthi 30 Nov 13 20:18 hs
-rw-rw-r — . 1 svimukthi svimukthi 12 Nov 12 12:09 sanka.txt
d — x — — — . 2 svimukthi svimukthi 20 Dec 13 18:53 test
/hms/apps is a directory
total 60
drwx — — — . 7 svimukthi svimukthi 4096 Dec 7 15:08 ajuba
drwx — — — . 7 svimukthi svimukthi 4096 Dec 7 15:08 ajuba-preference-data-loader
drwx — — — . 7 svimukthi svimukthi 4096 Nov 30 10:25 ajuba-survey
-rw-rw-r — . 1 svimukthi svimukthi 22772 Dec 10 17:01 sendKindle-2.1–6.el7.psychotic.noarch.rpm
-rw-rw-r — . 1 svimukthi svimukthi 19875 Dec 10 17:04 sendKindle-2.1–6.el7.psychotic.src.rpm
drwxr-xr-x. 2 svimukthi svimukthi 4096 Dec 17 08:24 Versions_Script
Exercise_9 - Write a shell script that displays, “This script will exit with 0 exit status.” Be sure that the script does indeed exit with a 0 exit status.
#!/bin/bash
echo “This script will exit with 0 exit status.”
exit 0
Output
[svimukthi@sanka Shell_Scripting]$ ./exe9.sh
This script will exit with 0 exit status.
Exercise_10 - Write a shell script that accepts a file or directory name as an argument. Have the script report if it is reguler file, a directory, or another type of file. If it is a directory, exit with a 1 exit status. If it is some other type of file, exit with a 2 exit status.
#!/bin/bash
FILE=$1
if [ -f $FILE ]
  then
    echo “It is reguler File”
    exit 0
elif [ -d $FILE ]
   then
     echo “It is directory”
     exit 1
 else
    echo “Another type”
    exit 2
fi
output
[svimukthi@sanka Shell_Scripting]$ ./exe10.sh /home/svimukthi/sanka
It is directory
Exercise_11 - Write a script that executes the command “cat/etc/shadow”. If the command return a 0 exit status, report “command succeeded” and exit with a 0 exit status. If the command returns a non-zero exit status, report “Command failed” and exit with a 1 exit status.
#!/bin/bash
cat /etc/shadow
if [ “$?” -eq “0” ]
  then
    echo “Command succeeded”
    exit 0
  else
    echo “Command failed”
    exit 1
fi
Output
[svimukthi@sanka Shell_Scripting]$ ./exe11.sh
cat: /etc/shadow: Permission denied
Command failed
Exercise_12 - Write a shell script that consists of a function that displays the number of files in the present working directory. Name this function “file_count” and call it in your script. If you use variable in your function, remember to make it a local variable.
#!/bin/bash
function file_count()
 {
   local NUMBER_OF_FILE=$(ls -l | wc -l)
    echo "$NUMBER_OF_FILE"
 }
file_count
Output
[vimukthi@vimukthi Test]$ ./coun.sh 
4
Exercise_13 - Modify the script from the previous exercise. Make the “file_count” function accept a directory as an argument. Next, have the function display the name of the directory followed by a colon. Finally display the number of files to the screen on the next line. Call the function three times. First on the “/etc” directory, next on the “/var” directory and finally on the “/usr/bin” directory.
#!/bin/bash
function file_count()
 {
   local Directory=$1
   COUNT_FILE=$(ls $Directory|wc -l)
   echo "$Directory"
   echo "$COUNT_FILE"
 }
file_count /etc
file_count /var
file_count /usr/bin
Output
[vimukthi@vimukthi Test]$ ./exe13.sh
/etc
295
/var
22
/usr/bin
2020
Exercise_14 - Write the shell script that renames all files in the current directory that end in “.jpg” to begin with today’s date in the following format: YYYY-MM-DD. For example, if a picture of my cat was in the current directory and today was October 31,2016 it would change name from “mycat.jpg” to “2016–10–31-mycat.jpg”.
#!/bin/bash
DAY=$(date +%F)
cd /home/vimukthi/Pictures
for FILE in *.png
 do
    mv $FILE ${DAY}-${FILE}
 done
After executing that script we can see change the names.
Exercise_15 - Write the script that renames files based on the file extension. Next,It should ask the user what prefix to prepend to the file name(s). By default, the prefix should be the current date in YYYY-MM-DD format. If the user simply press enter,the current date will be used. Otherwise,whatever the user entered will be used as the prefix. Next,it should display the original file name and new name of the file. Finally,it should rename the file.
#!/bin/bash
cd /home/vimukthi/Pictures
DAY=$(date +%F)s
echo "Pleace enter the file extension:"
   read EXTENSION
echo "Pleace enter the prifix:(press enter for $DAY)"
   read
for NAME in *.$EXTENSION
 do
   echo "Renaming $NAME to ${DAY}-${NAME}"
   mv $NAME ${DAY}-${NAME}
 done
After executing that script we can see change the names.
Exercise_16 - Created the start-up script for an application start and stop.
#!/bin/bash
INPUT=$1
cd /hms/installs/mongod/mongodb-linux-x86_64-2.6.0/bin
case $INPUT in
start)
       ./mongod -f ../../mongod.conf &
       echo "Mongodb server Start"
       ;;
stop)
      PID_ID=$(ps -ef | grep mongo | cut -d" " -f3 | sed '1!d')
      kill $PID_ID
if [ $? -eq '0']
      echo "Mongodb server Stop"
      ;;
*)
     echo "Error input"
     ;;
esac
Exercise_17 - Write the shell script that displays one random number on the screen and also generates a system log message with that random number.Use the “user” facility and “info” facility for your messages.
#!/bin/bash
MESSAGE="Random number is:$RANDOM"
echo "$MESSAGE"
logger -p user.info "$MESSAGE"
Run and check log
[root@vimukthi Test]# ./test.sh 
Random number is:13461
[root@vimukthi Test]# cat /var/log/messages | tail -n1
Jan 10 11:03:18 vimukthi vimukthi: Random number is:13461
Exercise_18 - Modify the previous script to that it uses a logging function. Additionally, tag each syslog message with “randomly” and include process ID. Generate a 3 random numbers.
#!/bin/bash
function logging()
  {
   MESSAGE=$@
   SET_MESSAGE="Random Number is:$MESSAGE"
   echo "$SET_MESSAGE"
   logger -i -p user.info "$SET_MESSAGE"
  }
logging $RANDOM
logging $RANDOM
logging $RANDOM
Run and check log
 [root@vimukthi Test]# ./exe18.sh
Random Number is:22009
Random Number is:25546
Random Number is:29800
[root@vimukthi Test]# cat /var/log/messages | tail -n5
Jan 10 11:20:01 vimukthi systemd: Removed slice User Slice of root.
Jan 10 11:20:01 vimukthi systemd: Stopping User Slice of root.
Jan 10 11:20:03 vimukthi vimukthi[6210]: Random Number is:22009
Jan 10 11:20:03 vimukthi vimukthi[6211]: Random Number is:25546
Jan 10 11:20:03 vimukthi vimukthi[6212]: Random Number is:29800
Exercise_19 - Write a shell script that exits on error and displays command as they will execute, including all expansions and substitutions. Use 3 ls command in your script. Make the first one succeed, the second one fail, and third one succeed. If you are using the proper options, the third ls command not be executed.
#!/bin/bash -ex
ls /hms
ls /hms/ms
ls /hms/apps
Output
[vimukthi@vimukthi Test]$ ./test.sh 
+ ls /hms
apps  backups  installs  logs  support Test
+ ls /hms/ms
ls: cannot access /hms/ms: No such file or directory
Exercise_20 - Modify the previous exercise so that script continuous, even if an error occurs. This time, all three ls command will execute.
#!/bin/bash -x
ls /hms
ls /hms/ms
ls /hms/apps
Output
[vimukthi@vimukthi Test]$ ./test.sh 
+ ls /hms
apps  backups  installs  logs  support Test
+ ls /hms/ms
ls: cannot access /hms/ms: No such file or directory
+ ls /hms/apps
ajuba  ajuba-preference-data-loader  ajuba-survey
