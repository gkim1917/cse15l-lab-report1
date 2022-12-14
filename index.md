# Tutorial of Remote Access and File System
### 09/30/22
### Lab Report 1
### Gunju Kim



## Step 1. Download the vscode
> ###  1. First go to this [link](https://code.visualstudio.com/) to download vscode.
## ![](vscode1.png)
> ###  2. After you download the vscode, the below screen will be shown.
## ![](vscode.png)




## Step 2. Remotely Connecting
> ### 1. Open the terminal in the vscode by clicking terminal>new terminal on the top bar of your Mac.
> ### 2. On the screen, type " ssh + (your own course account) ".
> ### 3. Enter your password for your course account.
> ### 4. If this is your first login, reply yes to the question, "Are you sure you want to continue connecting?"  
> ### 5. If your password doesn't work after few tries, change your password from the triton link. Try to save your password in a clipboard and try copying and pasting your password to use it later.
## ![](login.png)




## Step 3. Trying Some Commands
> ### Intro: In this step, I will introduce you some useful commands that you can use in terminal to copy the files and check the path of the current directory.
> ### 1. 'cd' changes the directory and 'cd ~' changes to the parent directory.
> ### 2. 'ls -lat' returns more detailed information about the list of contents in the current directory such as the username, time and the date of creation. 'ls -a' only gives the name of the contents in the current directory. If you login in your account, these commands will be useful in checking the overall or detailed version of the file structures of your remote computer.
## ![](command1.png)
> ### 3. 'ls' shows the list of files and directories in the current directoy. 
> ### 4. 'cp' copies the following file. 
> ### 5. 'cat' shows the content of the currnet file.
## ![](command2.png)
> ### 6. Enter 'exit' in order to log out from your server.




## Step 4. Moving Files with scp
> ### 1. First, create 'WhereAmI.java' file on your computer. This file helps you to differ the local computer to the remote one by informing you the name of the user, os, home, and directory.
```
class WhereAmI {
  public static void main(String[] args) {
    System.out.println(System.getProperty("os.name"));
    System.out.println(System.getProperty("user.name"));
    System.out.println(System.getProperty("user.home"));
    System.out.println(System.getProperty("user.dir"));
  }
}
```
> ### 2. Compile and run the file using 'javac' and 'java' command.
> ### 3. Open the terminal of the directory of this file and use 'scp' command to copy this file into the server.
```
scp WhereAmI.java cs15lfa22zz@ieng6.ucsd.edu:~/
```
> ### 4. Login to the server using 'ssh' command and check if the file is copied in the server using 'ls' command.
> ### 5. Compile and run the file using 'javac' and 'java' command again.
## ![](scp.png)
> ### In this screenshot, after logining into the remote computer, there are list of Cluster Status. I think the differences between the averages of each hostname might depend on the computers of the different servers. 




## Step 5. Setting an SSH Key
> ### Intro: SSH key helps you to create your public and private key for making the future use easier whenever you switch from local to remote computer.
> ### 1. On your desktop's terminal, enter "ssh-keygen". This will generate your public and private key.
> ### 2. Click 'Enter' if "Enter file in which to save the key" pops up.
> ### 3. Then, click 'Enter' if you want to login without entering password. (this will save more time!)
## ![](key.png)
> ### 4. Now, login in your course account and enter the password. Then make a new directoy, '.ssh' by entering 'mkdir .ssh'.
> ### 5. Enter 'exit' to log out from the server.
> ### 6. Now, copy your public key into the server by entering 'scp /Users/gunjukim/.ssh/id_rsa.pub cs15lfa22ne@ieng6.ucsd.edu:~/.ssh/authorized_keys'.
## ![](pass2.png)
> ### 7. If you login again using 'ssh', you no longer have to enter your password! (This actually saved me 30 seconds in changing and saving the file.)
## ![](passphrase.png)



## Step 6. Optimizing Remote Running
> ### The last step is helpful for students by saving their time in shortening the several lines of comments into one line.
> ### 1. The command can be used remotely on the same line of the screen by entering ssh, the name of the server, and the command line like the below example.
```
ssh cs15lfa22ne@ieng6.ucsd.edu "ls"
```
## ![](easy1.png)
> ### 2. More than one commands can be used in one line separated by semicolon.
```
cp WhereAmI.java; ls lab1; java WhereAmI;
```
## ![](easy2.png)