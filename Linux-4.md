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
This command is used to combine multioppe files into single file. 
and files that are combined with 'tar'command called tarball.
    - '-c' : to create archive datafiles.
    - '-x' : extract archive datafiles.
    - '-z' : Zip, to create ta date file by 'gzip'
    - '-v' : to display data.
    - '-t' : Tar -t : shows what is inside tar/zipped files. 
Ex: tar -cf firstTarbal.tar ./reversed1.txt ./reversed2.txt <---this creates a file and adds 2 files in it
[ec2-user@ip-172-31-16-200 ~]$ ls
allinfo         firstTarbal.tar   line_practice  reversed1.txt  reversedfile  test  zippedfiles
compressed.zip  greppractice.txt  linux.txt      reversed2.txt  servers.csv   z
[ec2-user@ip-172-31-16-200 ~]$ pwd
/home/ec2-user
[ec2-user@ip-172-31-16-200 ~]$ tar -xf zippedfiles ~/compressed.zip
[ec2-user@ip-172-31-16-200 ~]$ tar -tf ./compressed.zip
./firstTarbal.tar
[ec2-user@ip-172-31-16-200 ~]$ 


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

2. 







