# File Permissions 
* **Permissions**
    - `Read(r)`: Allows viewing the contents of the file.
    - `Write(w)`: Allows modifying the file. 
    - `Execute(x)`: Allows running the file as a program.
* **Permission Groups**
    - `Owner(u)`: The user who owns the file. Mostly it is the creator of the file. 
    - `Group(g)`: Users who are part of the file's group. 
    - `Others(o)`: Everyone else, who is not the owner of the file and not in the same group. 

* **Numeric Representation of Permissions**
    - 1 -> `execute`
    - 2 -> `write`
    - 4 -> `read`
    * **NOTE!** Find all other combination of permissions by adding numeric represantation of permissions. 

* `chmod`
    - `chmod` allows us to modify permissions of a file. We could either do it with numbers or we could do it using permission group and permission representations. 


* **Examples**
    - `Q`: Set a read and write permission for the owner, and set only read permission for the rest. 
```bash
chmod 644 filename
```
```bash
chmod u=rw g=r o=r filename
```
- `Q`: Add an `execute` permission for owner of the file only. 
```bash
chmod u+x filename
```
- `Q`: Remove read and write permission from group and others. 
```bash
chmod go-wr filename
```
* **NOTE!** `a` means all types of users for that file which includes, owner(u), group(g) and others(o). 

* **NOTE!**: If you want to change `directory and all contents of directory` at the same time use `-R` option(recursive).



# Users Management
- Users will be added to group with their name as default creation. 
- Such as `useradd newuser` command will set this newuser's main group as `newuser`.
- If user is added to groups later, user will inherit(take) all permissions from the group. 
- `useradd`
    * `-m` option: In some distros of linux, default home directory for the user is not created. To enforce this we could use `-m` option. 
    ```useradd -m newuser```
* `How do you view all users in the system? `
```bash
cat /etc/passwd
```
`/etc/passwd` contains one line for each user acct, with each line proivding information such as the username, password placeholder, userID,groupID, userinfo,homedirectory, login shell.

* **Switching Between Users**
- `su` -> substitute user(switch user).
```bash
su userName
```
- When switching user from non-root user acct. we have to provide other users password. 
- To set a passwd for the user:
```bash
sudo passwd userName
```

## Who can use sudo command in Linux? 
- Under `/etc` directory there is a file called
`sudoers`. In this file all users, and groups that has a `sudo` permission is written.
- In order to edit this file we could do:
    1. ```sudo visudo```
    2. ```sudo nano /etc/sudoers```

## Groups
- `groupadd groupName`
This command will create a new group.
- `groupdel groupName`
THis command will remove the group. 
- `usermod -aG groupName userName`
This will add `userName` to the group `groupName`


## Practice
*Prerequisites*
Starting as `ec2-user`
1. Create a group called devopsers
2. Create a user called devops1 with main group devopsers
3. Create another user called devops2 with main group devopsers
4. Create a directory in `home dir.` of devops1 with permissions set as: owner and group has all permissions and others don't have any permission.
5. Switch back to `ec2-user` and see if you can see the contents of the dir that you created. 
6. Switch to `devops2` and see if you can see the contents. Why or why not you can see it? 
7. See if we can do `sudo` command with `devops1` or `devops2` users
8. Add `devopser` group as a `sudoer` group
9. See now, if they `devops1` or `devops2` can use sudo command. Explain why or why not? 
10. Remove the `devops1` and `devops2` from the group called devopsers.
11. See if they can do sudo command now, why or why not? 
12. Remove the user `devops1` and `devops2` from the whole system.
13. Remove the group `devopsers` from whole system. 