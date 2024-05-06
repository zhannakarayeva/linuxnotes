# Linux Commands

1. ** TEE **
-Read from input and write to output and files.
It will put the outcome of the first command to another file. 
Ex:
Version 1
tac linux.txt > reversed1.txt
cat reversed1.txt
Version 2
tac linux.txt | tee reversed2.txt


2. ** CUT **
- it is used to extract sectoins from erach line of input, typically from a file. 
You specify which parr you want using options.
   - '-d'(delimiter): Specifies a delimeter  that separetes fields(defailt is one empty space)
   - '-f'(fields): Select the fields you want to extract (numbers)
   - '-c'(characters): Select the specifgic haracter position

   NOTE !
   Path Symbolis in Linux
    1. '~' -> This is short path of the 'home of the current user' Ex: cd ~
    2. '/' -> This is root 

** TAR **
This command is used to combine multippe files into single file. 
and files that are combined with 'tar'command called tarball.
    - '-c' : to create archive datafiles.
    - '-x' : extract archive datafiles.
    - '-z' : Zip, to create ta date file by 'gzip'
    - '-v' : to display data.
    - '-t' : Tar -t : shows what is inside tar/zipped files. 
    - '-cvf' : create single tarball file out of multiple files.
    - '-xvf' : extract files out of a tarball file.
    - 'tar -czvf newFile previousFile' : creates a compresed zipped file out of multiple files.
    - 'xzvf': extract files out of a zipped file.
    - '-tf':Displays the content of zip/tarball files
    - '-tvf':Dissplay the content of zip/tarball files with little more details
    - 'Order' of these options might be important in some cases.


# Combining Multiple Commands
1. ';' (semicolon)
-Used to separe multiple commands that will run sequetially, regardless of success or the failure of the previoius command.
- 'command1;command2' -command2 will run after command1 completes

2. && (And)
- used to run the second command only if the first command succeds.
- 'command1 && command2' - command2 runs only if the command1 succeds.

3. '||' (OR)
- used to run second command only if the first command 'fails'
- 'command1 || command2' -command2 run only if the command1 failed

4. '|' (Pipe)
- It will pass the output of the fst command as input to second command
- 'command1 | command2' 

-----------------------------------------------------------------------------------------------
## Managing Userd
SUDO Commands

1. 'useradd'
This command will add a new users 
Ex: sudo useradd testUser
Ex: id testUser 

2.  'useradd'
- This command will create a new user in the linux.







