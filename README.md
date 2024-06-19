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
    <img src="screenshots/question01_answer.png" width=700 height="auto"/>

    * ###### First one is easy, just type "systeminfo" and it gives to you all computer's basic information.