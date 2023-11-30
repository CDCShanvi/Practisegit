1. open cmd and create a new `.ssh` folder
   1. mkdir `.ssh`
   2. cd `.ssh`
2. ssh-keygen -t rsa -C yourcorporategit@curiousdevelopers.in -f CorporateUserID **(example:- ssh-keygen -t rsa -C nandan@curiousdevelopers.in -f CDCNandan)**
4. ssh-keygen -t rsa -C "personalemailid" -f PersonalUserID **(example:- ssh-keygen -t rsa -C gnnandan7@gmail.com -f gnnandan)**
5. if we get the error `Could not open a connection to your authentication agent`
   1. type services in windows search
   2. start the `OpenSSL Authentication Agent` and insted of disable option -> give authomatic option and start the services
6. open and run the git bash after that enter `eval ssh-agent -s`
7. `ssh-add CorporateUserID` **(example:- `ssh-add CDCNandan`)**
8. `ssh-add PersonalUserID` **(example:- `ssh-add gnnandan`)**
9.  Create A Conf File
   1. touch config
   2. add the below configuration in config
```
#corporate
Host corporate_userid
    HostName github.com
    User git
    IdentityFile ~/.ssh/corporate_userid

#personal
Host personal_userid
    HostName github.com
    User git
    IdentityFile ~/.ssh/personal_userid
```
**Example**
```
#Nandan office account
Host CDCNandan
    HostName github.com
    User git
    IdentityFile ~/.ssh/CDCNandan

#Nandan personal account
Host gnnandan
    HostName github.com
    User git
    IdentityFile ~/.ssh/gnnandan
```
10. Add the public key in your remote git repository
   1. go to `settings` then -> `ssh and gpg` option then -> add new `ssh` by copying from corporate_id.pub file in `.ssh` folder 
   2. you can start cloning
11. Cloning And Taking Latest Pull Steps
   1. Create a directory on your desktop
   2. go inside the directory
   3. Cloning Steps
      1. enter `git clone git@CDCUserName:Curious-Ecosystem/Mentor-Mentees-Connect.git`
      2. `ls` and go inside the directory
      3. cd `Mentor-Mentees-Connect`
      4. enter the `git pull` command
