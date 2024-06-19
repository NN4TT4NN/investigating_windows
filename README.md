<img src="https://tryhackme-images.s3.amazonaws.com/room-icons/ca912860a1629510138df1b796ae687f.png" width=100 height="auto"/>

# [Investigating Windows](https://tryhackme.com/r/room/investigatingwindows) 

This repository is dedicated to show how i go through Hacking challenges.
Created only for learning pourposes and all the solutions and tricks are used at controlled environments.
Happy Hacking 😃

A windows machine has been hacked, its your job to go investigate this windows machine and find clues to what the hacker might have done.

Connect to the machine using RDP. The credentials the machine are as follows:

###### Username: Administrator

###### Password: letmein123!

#### So let's get started phreaks 🕵️‍♂️

* If you're going to connect to the Windows machine remotely, don't forget to setup your VPN config file and make shure your connection is running, good? 👍
  
* First of all, i'll be connecting to the remote windows machine using RDP, but you can just start the Windows machine at [Try Hack Me](https://tryhackme.com/r/room/investigatingwindows) by clicking the green "Start Machine" button 💡


#### I'm at a Kali Linux Machine, so the command is ⬇️
  
````
xfreerdp /v:<victim_machine_ip> /u:Administrator /p:letmein123!
````

<img src="screenshots/setup_rdp.png" width=700 height="auto"/>
<img src="screenshots/setup_rdp_scr_width.png" width=700 height="auto"/>

* You'll be asked if you wanna trust the certificate, make shure you type "y" and click enter 👍
* There's also a width and height option that you can pass if you want.

<img src="screenshots/windows_initial_screen.png" width=700 height="auto"/>


### Questions

1. ###### Whats the version and year of the windows machine?
    <img src="screenshots/question01.png" width=700 height="auto"/>
    <img src="screenshots/question01_answer.png
    
    
    
    
    " width=700 height="auto"/>

    * ###### First one is easy, just type "systeminfo" and it gives to you all computer's basic information.


2. ###### Which user logged in last?
    * For this one first we need to know how many users are in the victim's machine.
    * The command for this is the following:
  
        ````
        net user
        ````
    <img src="screenshots/listing_accounts.png" width=700 height="auto"/>

    * Now you know all of them!
    * And it takes us to the next command to see who logged in before us.
    * There's many ways you can do this specially in Windows machines, navigating by the interface.
    * But, we are hackers, we should really know how to manage different commands into any terminal.
    * The command below, shows the login of the "administrator" user  ⬇️
    ````
    net user "administrator" | findstr /B /C:"Last logon"  
    ````
    <img src="screenshots/adm_last_logon.png"/>

    * But, just like i said, we're hackers, we want something more.
    * So let's create a script to return all users last logins into our terminal:
    
    ````
    @echo off

    for %%u in (John Administrator Jenny Guest DefaultAccount) do (
        echo %%u:
        net user %%u | findstr /B /C:"Last logon"
        echo.
    )

    ````
    * First we need to know where we are, do let's run a dir:
    
    <img src="screenshots/dir.png" width="700"/>

    * You can change directories if you want, but i'm kipping this one.
    * Now lets create the file :
    ````
    echo "hello" > check_logon.bat
    ````
    <img src="screenshots/create_check_logon_file.png" width="700"/>

    * Now you can open notepad and start creating your script:
    ````
    notepad check_logon.bat
    ````
    <img src="screenshots/opened_notepad.png" width="700"/>
    <img src="screenshots/bat_script.png" width="700"/>

    * Save the file.
    * Now go back to the terminal and run the file:
  
    <img src="screenshots/script_output.png" width="700"/>

    * And there it is, our last logged in user is "Administrator":

    <img src="screenshots/question02_answer.png" width="700"/>

3. ###### When did John log onto the system last?
   
   * The answer for this one is in the last answer:

    <img src="screenshots/john_last_logon.png" width="700"/>
    
    <img src="screenshots/question03_answer.png" width="700"/>
  

3. ###### What IP does the system connect to when it first starts?
   
   * For this you need to watch when the you start the machine, there will be an ip showing up to the screen.

    <img src="screenshots/first_ip_conn.png" width="700"/>

    <img src="screenshots/question04_answer.png" width="700"/>
