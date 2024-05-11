# Managing Users and Groups
- **Deleting user from a group**
    * `sudo deluser username groupname`
    When using distros based on debian or ubuntu. 
    * `sudo gpasswd -d username groupname`
    When using distos based on fedora, centos, rhel etc.



1. **echo** 
    - This command prints out the given text in shell output. 
        - `echo something`
        You will see `something` on the shell output. 
        - `echo 'something'`
        You will see `something` on the shell output. 
        - `echo "something"`
        You will see `something` on the shell output. 
# Regular Expressions(RegEx) in Linux
- Regular expressions are used to find patterns from a file or any given text in linux. 
- In order to use `grep` command with regular expressions and more complex commands we could use `-P` option. 
`grep -P 'regex'`

1. Find the lines that start with `^`
```bash
grep -P '^t'
```
2. Find the lines that end with `$`
```bash
grep -P 'e$'
```
Finding all the lines that end with e

3. Matching Multiple Characters at once
```bash
grep -P '[cdte]'
```
This matches with all c,d,t,e in the file. 
[a-z] means all letters
[0-9] means all numbers
[A-Z] means all uppercase letters

4. Quantifiers
- These will specify how many instances of a character, group, or character class must be present in target match.
    * `*` mathces 0 or more times
    * `+` mathces 1 or more times
    * `?` matches only 0 or 1 match
```bash
grep -P "a[0-9]*" filename
```
- This will match with `a` or `a1` or `a91` or `a1000` etc.

```bash
grep -P "a[0-9]+" filename
```
- This will match with `a1` or `a91` or `a1000` etc.

```bash
grep -P "a[0-9]?" filename
```
- This will match with `a` or `a1`.

- We could also match with exact number of occurences
```bash
grep -P "[0-9]{2}" 
```
This will find exactly 2 numbers as a match.

5. Grouping and Alternating
- I want to find 2 matches of a word, or other group of 
characters then I have to group those characters with parentheses. 


```bash
grep -P "berry{2}" filename
```
- Line above will match with `berryy`.
```bash
grep -P "(berry){2}" filename
```
- Line above will matach with `berryberry`.

* Choosing one or the other word
```bash
grep -P "(berry|tomato)" filename
```
- This will match with berry or tomato

##
6. Finding the match as a word not part of a bigger word.
```bash
grep -P "\b(berry)\b" filename
```
this will find the berry as a word not part of another word. 

7. Finding any matching character
```bash
grep -P "a.ple" filename
```
This will match with `atple` or any character instead of `.`.

# Variables and Environment Variables In Linux
* **Creating Global Variables**
- On the shell you could assign a value to the name. 
- No space and quotations are not necessary.
```bash
home_dir="/home/ec2-user"
```
- Whenever you want to use `value` of the variable, call the variable with `$` in front of the variable name. 
- Creation of these variables are temporary, if we want to make it persistent we have to add them to the `/etc/profile` file or `./bashrc` file under our user's home directory. 

- These variables are not accessible in other shell processes such as child shells etc. 

* **Creating Global Environment Variables**
- On the shell you could assign a value to the name. 
- No space and quotations are not necessary.
```bash
export home_dir="/home/ec2-user"
```
- Whenever you want to use `value` of the variable, call the variable with `$` in front of the variable name. 
- Creation of these variables are temporary, if we want to make it persistent we have to add them to the `/etc/profile` file or `./bashrc` file under our user's home directory. 
- When `environment` variables are created they are accesible on `subshell` processes but they are not accessible on other shell processes(for different user's shells.)


# Bash Files
- Instead of running each command one-by-one we could store all the commands in a file and execute those commands all together. 

- **NOTE**: It is a custom to add the shell process that you want your bash file to be executed in first line of your bash script. This is not necessary to execute bash files. 
```
#!/bin/bash
```
`#!` is called `shebang` symbol.
- **NOTE**: To create a comment in the bash file we could use
`#` symbol. Lines that start with `#` symbol will not run on the shell. 

## Once a bash file is created there is 3 ways to run:
1. You could run in `subshell` process by using `bash`
command. 
```bash
bash filename
```
2. You could run the file using the location of the file and this will run the file in a `subshell`. To be able to 
run the file by its location the file has to be executable.
```bash
/home/ec2-user/bashPractices/bash1.sh
```
3. You could run the file using `source` or `.` command
and this will run the file in current shell process. 
```bash
source filename
```
or 
```bash
. filename
```