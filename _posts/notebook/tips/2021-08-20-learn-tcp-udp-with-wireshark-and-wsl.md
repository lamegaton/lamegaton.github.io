---
layout: post
title: TCP/UDP Flow Analysis with Wireshark and Windows Subsystem for Linux
categories: tips
author: "Son Pham"
meta: Learn TCP or UDP flow by using Wireshark and Windows Subsystem for Linux
description: "Learn TCP or UDP flow by using Wireshark and Windows Subsystem for Linux"
comments: false
---

During many of my interviews, I have been asked whether I understood TCP and UDP, and how they differed from each other. While I knew that TCP had an error-checking procedure that made the protocol more reliable but slower than UDP, my understanding was limited. Although I had learned about the detailed structure of these protocols in school, I didn't have a chance to get hands-on experience with them. However, I later discovered an easy way to explore TCP and UDP packets using Windows Subsystem for Linux (WSL) and WireShark. As a result, I would like to share what I have learned today.

----

Table of Contents:

* Placeholder for Table of Content (Must not be removed)
{:toc}

# Setup TCP client and server with NetCat  
## 1. Install netcat  
In WSL  
	```sudo apt-get install netcat```  
To know the argument for netcat or nc you can use  
	```man netcat```  
  
#### 2. Install Wireshark  
  
#### 3. Setting up Wireshark  
Open Wireshark and select `Adapter for loopback traffic capture`  
In the `Apply a display filter` box type `tcp.port == 5000` because we will use port 5000 for transmitting and receiving.  
  
#### 4. Setting up TCP/UDP server and client  
You can open 2 WSL windows, one for client and the other for server  
- TCP:  
server  
	```nc -l localhost 5000```  
This means listen with TCP at port 5000 on localhost  
client  
	```nc -v localhost 5000 <<< 'sup buddy'  ```  
If it is successful, it will show  
	```Connection to localhost 5000 port [tcp/*] succeeded!  ```  
- UDP:  
server  
	```nc -l -u localhost 5000  ```  
client  
	```nc -v -u localhost 5000 <<< 'sup buddy'  ```  
Alternatively, you can also try the command `cat textfile > /dev/tcp/HOST/PORT` to send message to the server  
  
#### 5. Checking Result on Wireshark  
If you follow all of the steps correctly, you will see 3 ways handshake and all the payloads that come with it.  
![2021-08-25 22 23 18](https://user-images.githubusercontent.com/5988492/130905620-9c1b2282-4a92-40d6-abc6-d342e71d66f1.png)  
  
Also, you can go to **Statistics > Flow Graph** under **Flow Type** select **TCP** to see the flow of traffic  
![2021-08-25 22 27 29](https://user-images.githubusercontent.com/5988492/130905976-423568fc-8111-4e90-82d5-2571addac235.png)

  
