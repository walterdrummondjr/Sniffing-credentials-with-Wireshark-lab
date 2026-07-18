<h1>Sniffing-credentials-with-Wireshark</h1>





### Description
This lab walks you through capturing HTTP traffic with Wireshark, analyzing the packets, and finding user login credential.
<br />



### Tools and Utilities Used:


- <b>Wireshark</b>




### Environment Used:

### Oracle Virutal Box:

  
- **VM machine** = Ubuntu 26.04 LTS




### Knowledge Gained:

- **Web development** (Using PHP language to setup PHP website on Apache server. Managing Apache server: navigating Apache web server directories, restart Apache server)

- **Using Wireshark** (Analyze HTTP traffic to sniff passwords)


<br><br>


<h1>Lab Setup:</h1>

### Run command to install the PHP programming language and Apache module that integrates PHP with the Apache web server:

sudo apt install php libaapache2-mod-php  

<img width="1180" height="622" alt="Image" src="https://github.com/user-attachments/assets/279f6c08-2afd-4692-a7d4-dd2689d03aaf" />
<br><br>

### Configure PHP website:

**Information:** Create a PHP file. This PHP script gives the website a form so a user can login with their username and password. Sets a title for this page.

### Created and named the file login.php:

<img width="936" height="361" alt="Image" src="https://github.com/user-attachments/assets/8e18a80b-5296-4fc2-83bb-fac1ca89affb" />

<img width="1246" height="700" alt="Image" src="https://github.com/user-attachments/assets/8b96bb0c-7965-41a4-92f0-d7b01f0f9116" />

<img width="1270" height="689" alt="Image" src="https://github.com/user-attachments/assets/e22c3396-c3b9-41ad-8d82-63442bd635db" />
<br><br>

**Results:** Save login.php file.
<br><br>


**Information:** Create a PHP file. This PHP script checks if the user is authorized. If not, it directs the user back to the login page. Sets a title for this page and sets images on the page. Sets a title for the user that is currently logged in. All files will be saved in the /var/www/html directory. This is the default root Apache web server directory. This is where website files are placed.
<br><br>


### Created and name file landing.php:


<img width="822" height="278" alt="Image" src="https://github.com/user-attachments/assets/d500b8ce-0867-4003-adc9-78d23bc81713" />

<img width="1268" height="690" alt="Image" src="https://github.com/user-attachments/assets/307da06a-b698-4b82-b1d0-aa6f5f369784" />

<img width="880" height="393" alt="Image" src="https://github.com/user-attachments/assets/be5bebf1-6e56-43c9-a030-f6498ead27a0" />
<br><br>

**Results:** Save landing.php file.
<br><br>


**Information:** Create a PHP file. This PHP script clears all user session data and returns them to the login page.
<br><br>


### Created and name the file logout.php:

<img width="655" height="192" alt="Image" src="https://github.com/user-attachments/assets/4b1de04b-9b17-4c79-90df-6cd003ad15ed" />

<img width="704" height="321" alt="Image" src="https://github.com/user-attachments/assets/b26f2060-6fa3-4bda-b872-f385748011e2" />
<br><br>


**Results:** Save logout.php file.
<br><br>


### Restart Apache server:

systemctl restart apache2

<img width="805" height="203" alt="Image" src="https://github.com/user-attachments/assets/59f03790-3da9-40e2-a579-41feb2004d59" />
<br><br>








<h1>Lab:</h1>

**Scenario =** A bad actor has compromised this server and is running Wireshark to capture network traffic. TCPDump tool can also be used to capture network traffic. User logs into the PHP site the bad actor captures users credentials.
<br>

### In the terminal type: wireshark 


<img width="867" height="218" alt="Image" src="https://github.com/user-attachments/assets/2f556069-7b7f-4553-87f1-e0f06111e2ae" />
<br><br>




### Wireshark launches, make sure wireshark has the interface you want to capture traffic on:  

<img width="1281" height="763" alt="Image" src="https://github.com/user-attachments/assets/50bf98d5-b216-4ff0-aaf3-4fb41de031ff" />
<br><br>


**Note:** For this example, the PHP website is running on local host (127.0.0.1) loopback interface.
<br><br>

### Press start button to start capturing packets:

<img width="1283" height="771" alt="Image" src="https://github.com/user-attachments/assets/5c5ac7ce-356a-4fce-9a78-732c3f314ea6" />
<br><br>

### User goes to the website to login with credentials:

<img width="1256" height="745" alt="Image" src="https://github.com/user-attachments/assets/089c036f-bf91-4a1f-83fa-a6546b9106d8" />
<br><br>


### The user has successfully logged into the website:

<img width="1277" height="707" alt="Image" src="https://github.com/user-attachments/assets/c63b0666-1559-43e1-8b13-70efa3e9cbb9" />
<br><br>

### To stop capturing traffic in wireshark,  press stop button:

<img width="1285" height="769" alt="Image" src="https://github.com/user-attachments/assets/9abacd63-3df7-4be4-993b-17d4b0a3a3f2" />
<br><br>

### Go to the filter box underneath wireshark tool bar and type: http and press enter:

<img width="1282" height="648" alt="Image" src="https://github.com/user-attachments/assets/ac8dc0a1-4447-4454-a757-93401c41e574" />
<br><br>

### Now we can see all HTTP packets:

<img width="1279" height="375" alt="Image" src="https://github.com/user-attachments/assets/4d8ab466-626d-43c8-af33-d699d1edf2da" />
<br><br>


**Information:**  We can see a HTTP packet with a POST request. A HTTP POST request is used to send data to the web server.

**POST request can also be filtered by using filter expression:** http.request.method == "POST" **and press enter:**

<img width="1287" height="573" alt="Image" src="https://github.com/user-attachments/assets/20bdd488-ced1-4940-aad4-6de40c263f01" />
<br><br>


### Click on the HTTP packet with the POST request:

<img width="1288" height="838" alt="Image" src="https://github.com/user-attachments/assets/f4bdb456-7db1-4062-9d07-8c9212020713" />
<br><br>

### Go to the packet detail pane lower right hand side of wirehshark:

<img width="1280" height="737" alt="Image" src="https://github.com/user-attachments/assets/087e4d4d-1c30-4e3b-88b6-97c7955bbc29" />
<br><br>


**Information:** We can see different Protocol's in this section. Underneath the HTTP protocol we can see HTML form URL Encoded: application/x-www-form-urlencoded. This section displays data sent from the PHP website form to the web server using application/x-www-form-urlencoded format. This section shows the text the user typed into the form fields (username and password).

### Click on the tab on that field to show the information:


<img width="1241" height="764" alt="Image" src="https://github.com/user-attachments/assets/022ca749-339b-4a12-9dbe-3720bc6a7c4e" />

<img width="1290" height="643" alt="Image" src="https://github.com/user-attachments/assets/d4f78b16-d51d-4a71-82bb-972fce2c8ae7" />
<br><br>

**Results:** The username and password values are in clear text. This is because the site is using HTTP protocol which does not use encryption. 


<h1>Conclusion:</h1> This is why you should use HTTPS instead of HTTP. All HTTPS communication between the browser and the web server is encrypted (TLS encryption). HTTP transmits data in plain text, which means anyone sniffing the network can read the data.






































