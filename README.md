# HTI-Storage-Server
This a simple walkthrough to our project, with steps on how to get it installed and running.
The project was done on both Windows OS, and Linux OS, so better to setup a virtual Box for Linux


# Installing Kali Linux

1. Virtual-Box Download link (106MB): [Virtual-Box Download](https://download.virtualbox.org/virtualbox/7.0.12/VirtualBox-7.0.12-159484-Win.exe)
2. Kali Linux Pre-built Virtual Machine (3.1GB): [Kali Linux Pre-Built VM](https://cdimage.kali.org/kali-2023.4/kali-linux-2023.4-virtualbox-amd64.7z)
- Then Follow this video: [Youtube Video to install Kali](https://youtu.be/iu-puVuUuzU?t=120)



# OPTIONAL
# Installing Windows VM
If you want to create a virtual windows machine just for the project, 
you can do that by following this video: [Youtube video to install Windows VM](https://www.youtube.com/watch?v=sBzL_zoYt6o)



# Project Installation

1. Download "Project Files.rar", and extract it on desktop. "[Project File contents](https://i.imgur.com/TXzu9tg.png)"
2. Download Xampp, Snort, and Npcap and install them to default directories. "download links in the .txt files"
3. Extract "filehosting Database" in desktop. "[filehosting.sql](https://i.imgur.com/c6b4Vsv.png)"
4. After installing Xampp, open it, launch both Mysql + Apache servers, and click on the "Shell" icon on the right side
5. in the shell type the next code:
      - ```
          mysql -u root -p
        ```
   - you will be asked to enter a password, just press enter, you will enter the Mysql databse, enter the next code to create a Database:
      - ```
           create Database filehosting;
        ```
   - Verify that you have successfully created a database with this command
     - ```
           show databases;
         ```
     [Should look like this](https://i.imgur.com/qQY9R8l.png)

   - Finally, exit our of the Mysql by typing
      - ```
           exit
        ```
   - Back in the main Shell command prompt, type the next command
      - ```
           cd %userprofile%\Desktop
           mysql -u root -p filehosting < filehosting.sql
        ```
   - this should import the pre built database, to the database you just created.

6. Extract the "file-hosting Website.rar" file to this directory "C:\xampp\htdocs" 
7. Enter the website with this [Link](http://localhost/file-hosting)

the website should be ready to use at this moment.






# SNORT Installation

1. Extract the "Extract to snort.rar" file to the snort directory "C:\Snort", make sure to Replace all the files "[Like this](https://i.imgur.com/NFB7Tgq.png)"
2. Get your ip, by opening cmd, and typing ``` ipconfig ```, copy the IPV4 "[This one](https://i.imgur.com/OiMknxY.png)"
3. goto "C:\Snort\etc" and open the "snort.conf" with notepad, and replace this ip under the "step #1" with your ip "[Exact location](https://i.imgur.com/QIKNuck.png)"
4. Open cmd, and type the next command:


- ```
  cd c:\Snort\bin
  snort -i -1 -c c:\Snort\etc\snort.conf -T
  ```

- It should run with no erros, after that you need to know your Interface that your going to work with, type the next command to find out
- ```
  snort -W
  ```
- you should see different interfaces, but only one with the same IPv4 you entered in the snort.conf before "[Example](https://i.imgur.com/o2KVZan.png)"
Now, you can start the snort tool with this command
- ```
  cd c:\Snort\bin
  snort -i 1 -c c:\Snort\etc\snort.conf -A console
  ```
- make sure that this part "snort -i 1" is the same number as your interface.
- Now snort is running, and waiting for packets to analyze.



# Python Script installation

1. Launch the linux machine, login with username and password "kali" for both.
2. Copy the "Python Script" from your windows to the Linux machine "[Link to Directrly Download on Linux](https://file.io/qZ01sOxiZuwh)"
3. open a Terminal, and type the next commands

      - ```
            cd Downloads
            unzip Python\ Script.zip  -d /home/kali/Desktop/
        ```

- The file should be extracted to desktop, Run this commands to launch the script
- ```
      cd /home/kali/Desktop/Python
      python PythonScript.py
  ```

- Voila! you should have the script running.
