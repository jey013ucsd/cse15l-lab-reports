# INSTALLING VISUAL STUDIO CODE



![image](https://user-images.githubusercontent.com/114262093/193373251-babb9c46-64ee-4528-8a79-39b77f4dd1ca.png)

* Navigate to https://code.visualstudio.com/ and download
* Launch the downloaded file and install vscode






# REMOTELY CONNECTING



![image](https://user-images.githubusercontent.com/114262093/193374575-7238070b-a6be-4d85-8c48-8a0ba54f5c47.png)

* Navigate to the account lookup tool(https://sdacs.ucsd.edu/~icc/index.php) to find your cse15L account
* Identify your username: "cs15lfa__"

![image](https://user-images.githubusercontent.com/114262093/193374327-a18f6da7-abf0-4afa-9991-4d7ba2fb3411.png)

* In the terminal run the command `$ ssh cs15lfa22hp@ieng6.ucsd.edu` using the username found above
* Enter your password to connect to the server




# TRYING SOME COMMANDS


![image](https://user-images.githubusercontent.com/114262093/193375572-3dc2c488-81ed-4e4d-8f00-1c8353d6829d.png)

* Try out some commands such as: 

```
$ cs ~
$ ls -lat
$ ls -a
$ ls /home/linux/ieng6/cs15lfa22/cs15lfa22<username>
```





# MOVING FILES WITH SCP



![image](https://user-images.githubusercontent.com/114262093/193375872-4dac9828-4ad5-43c3-960a-7e04bb80107b.png)

* Create a new notepad document and copy and paste WhereAmI code
* Save file as "WhereAmI.java"

![image](https://user-images.githubusercontent.com/114262093/193375915-36ffd99f-af37-4538-bd48-f323f1b7c42e.png)

* In the terminal, run `$ scp WhereAmI.java cs15lfa22zz@ieng6.ucsd.edu:~/` to copy the file onto the server
* Enter password
* To check that the it was copied succesfully, log back in and run:

```
javac WhereAmI.java
java WhereAmI
```






# SETTING AN SSH KEY

* Run `$ ssh-keygen` and press enter whenever prompted
* Open Windows Powershell as adminstrator
* Run the following coommands: 

```
Get-Service ssh-agent | Set-Service -StartupType Automatic
Start-Service ssh-agent
Get-Service ssh-agent
ssh-add $env:USERPROFILE\.ssh\id_ed25519
```

![image](https://user-images.githubusercontent.com/114262093/193376074-7343e88e-b05b-40a8-a9ff-9863b0857dea.png)

* Log into server and run `$ mkdir .ssh`
* Log out and run `$ scp /Users/coolj/.ssh/id_rsa.pub cs15lfa22hp@ieng6.ucsd.edu:~/.ssh/authorized_keys`
* To ensure it is working, try to log back in and it should not require a password




# OPTIMIZING REMOTE RUNNING

![image](https://user-images.githubusercontent.com/114262093/193376254-a5ff8db5-b6e8-4352-a5a8-0c891207e330.png)

* Commands can be ran without having to log into the server
* Add the command in quotation marks after `ssh cs15lfa22hp@ieng6.ucsd.edu`
* Screenshot is an example using ls


![image](https://user-images.githubusercontent.com/114262093/193376355-f22c1b4d-006c-4b1b-829d-a69ee7b57871.png)

* Multiple commands can be run on the same line by adding a semicolon in between them
