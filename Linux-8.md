## Linux Comparisons Part II

1. **Text(string) Comparison Operators**
    - `==`: equal
    - `!=`: not equal
    - `-z`: string(text) is empty(null) no characters
    - `-n`: string is not null(empty)

* To check multiple conditions with `if` statement we could 
use `if-elif-else`.
```bash
if [ condition1 ]; then
   # command to execute when condition1 is true
elif [ condition2 ]; then
   # command to execute when condition2 is true and
   # condition1 is false.
else
   # command to execute when all conditions above is false
fi
```
* **Logical Operators In Bash**
- `&&`: And operator -> All of the given conditions must be true to continue.
- `||`: Or operator -> One of the given conditons being true
is enough to continue. 
**NOTE!**: Using double brackets in scripting allows us to use reg-ex in string comparisons.  `[[ condition ]]`

* **File Comparison in Bash Scripting**
**File Test Operators**
1. `-f`: Will check if the file exists and a regular file.
2. `-d`: Will check the file exists and it is a directory.
3. `-s`: Will check the file exists and it is not empty.
4. `-r`,`-w`,`-x`: File exists and is readable, writable or executable respectively. 
```bash
if [ -f "$filepath" ]; then
    echo "It is a file and exists."
fi
if [ -d "$filepath" ]; then
    echo "It is a directory and exists."
fi
if [ -s "$filepath" ]; then
    echo "file exists and not empty"
fi
if [ -r "$filepath" ]; then
    echo "file is readable"
fi
```

```txt
Ask user name(read or command line arg.)
Ask the file name
Ask the group name
- Check if the user is in the group.
- Check if the user can write on the file(You could assume that user owns the file.)


```

## NOTES
- If statements actually work with `exit status code` of the
commands. If an exit status code `0` it means the code executed successfully. Anything other than `0` means unsuccessful code execution.
- If you want to assign value of your command to a variable
you have to put command inside a parantheses.Such as
```bash
var=$(pwd)
echo $var # this will print the current working directory.
```
- If we want to stop our bash script prematurely we could use `exit` command. `exit` command will stop our script immediately and will not execute anything after in that script.We could also provide specific exit codes depending on if our script is successful or not at that point. Such as 
`exit 1`, `exit`, `exit 2` ...
- `echo $?` will print the exit status code of the last executed command.

# More linux commands
1. `wc` 
    * Word count command is used to count lines, words and bytes in a file. 
    - `wc filename`: It will give you the total number of words in a file. 
    - `wc -l filename`: It will give you the total number of lines in a file. 
    - `wc -c filename`: It wil give you the total bytes in a file. 

2. `du`
    * Estimate file space usage, the space used under a particular directory or files on a filesystem. 
    - `-h`: to get the usage in human  readable format.
    - `-s`: Summary of the directory's size. 
    - `-a`: Show all usage of files not just directories
3. `sort`
    * It will sort given info in ascending order.It will sort it alphatically.
    - `-g`: Option will sort by the numerical values. 
4. `df`
    * Disk free command is used for reporting the amount of disk space used and available on file systems. 
    - `-h`: Human readable sizes
5. `systemctl`
    * It is used to examine and control the systemd system and service manager which is responsible for controlling how services are started, stopped and managed on modern linux distributions. 
    - `systemctl start servicename`-> starts the service
    - `systemctl stop servicename`-> stops the service
    - `systemctl restart servicename`
    - `systemctl status servicename` -> Current activity status on the service whether it is active or not.
    - `systemctl enable servicename` -> When a service is enabled, it will automatically start after reboot. 
    - `systemctl disable servicename` -> cancels out the service start at boot. 
    - Usage of systemctl with if statements
```bash
if [ systemctl is-active --quiet servicename ];
then
    # this line will be executed when the service is active
fi    
```
6. `package managers`
    * Package managers are used to install and manage applications(services) to our linux. 
    - `AWS Ec2 linux 2023` distro used `yum` as a package manager. 
    - `Ubuntu` uses `apt-get` as a package manager
    - Updating all installed packages in linux distros:
    `sudo packagemanager update`

    - when installing a package if you don't want to press `y` for every question manually, you could add `-y` at the end of the command so it will auto answer `yes` to each question.
-- install `nginx` package to linux and start the service. 
and make sure this service will still run after a reboot.