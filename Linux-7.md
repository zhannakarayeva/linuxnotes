# Linux Command Line Arguments

- For accessing command line arguments we could use 
`$` and number. 
    `$1` is going to access the first command line argument
    `$2` is going to access the second command line argument
    .....
    `$@` is all command line arguments
    `$#` is the number of arguments given to the file

## Creating Your Own Command
- All of the commands that we use are file.They are bash files. Since they are executable we are able to run them. 
Because they are in the `PATH` env. variable we do not need to provide exact location of those files. 
`PATH` env. variable stores location of all runnable files. When we write a command, linux looks at all those locations and tries to find the file. If it does then it executes, otherwise it will say no command found. 

* In order to create my own command I either have to move my file to one of the locations in `PATH` env. variable. **OR**
I could add location of my file to the `PATH` env. variable. 

```bash
export PATH="$PATH:/home/ec2-user/bashpractices"
```

# Making Env. Variables Persistent
1. **Creating in `~/.bashrc`**
- Every time user opens the shell(or logs back in) the       `.bashrc` for that user is going to run.
- `bashrc` stands for `bash run commands`
- The variables defined in `~/.bashrc` files are user specific. And these variables become available whenever user opens a bash shell. 

2. **Creating in `/etc/environment`**
- This file is sytem-wide; any variables set here are available to **ALL** users.
- Variables set here are loaded at login and are available in the whole system environment, including desktop sessions. 
- Used for setting variables that need to be accessed among all users system wide, not tied to shell instances. 
- **NOTE!** Become a root user`sudo su`.
```bash
echo "export syswide=\"This variable is accessible by all users\"" >> /etc/environment
```
## Read Command
- The `read` command is used to real a line of input from shell. It assigns the input to a variable. 
When executed this command will pause the execution and wait for the user to enter some input. 

* `-p` Prompt string. Allows you to specify a prompt that is displayed to the user. 
```bash
read -p "Enter your user name: " uname
```
* `-s` Silent mode. Doesn't echo the input back to console. THis is particularly useful for passwords. 
```bash
read -s -p "Enter your password: " pswd
```
* `-t` Timeout. you could limit how lonag you will wait till user finishes typing. 
```bash
read -t 15 -p "You have 15 sec. to write your address"
```
* ..
    **NOTE!** If you time out the variable is assigned with empty value. 

## If Statements in Linux Bash
- If statement in bash scripting is fundamental for decision making. Using if, we could allow script to execute commands based on whether certain conditions are `true` or  `false`. 

* **SYNTAX**

```bash
if [ condition ]
then
    # Commands to execute when condition is true
fi
```
* **How do we create conditions in bash scripting?**
1. **Comparison Operators**
    - **Numerical Comparison Operators**
        * `-eq`: equals
        * `-ne`: not equal
        * `-gt`: greater than
        * `-ge`: greater than or equal to
        * `-lt`: less than
        * `-le`: less than or equal to
```bash
if [ 5 -le 6 ]
then
   echo "5 is less than or equal to 6"
fi
# this code above will output `5 is less than or equal to 6`
```