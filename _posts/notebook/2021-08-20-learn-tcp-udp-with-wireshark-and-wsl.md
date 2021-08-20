---
layout: post
title: Learn TCP or UDP flow by using Wireshark and Windows Subsystem for Linux
categories: en tip
author: "Son Pham"
meta: Learn TCP or UDP flow by using Wireshark and Windows Subsystem for Linux
description: "Learn TCP or UDP flow by using Wireshark and Windows Subsystem for Linux"
comments: true
---

Many of the interviewers have asked me if I understood TCP and UDP, and what are the differences between them. The only thing that I know is that TCP has an error-checking procedure which makes the protocol more reliable and slower than UDP. At school, I was taught the detailed structure but did not have a chance to hand-on. Later, I figured out an easy way to explore TCP and UDP packets with Windows Subsystem for Linux (WSL) and WireShark. So today, I will share what I have learned here.

# Setup TCP client and server with NetCat  
## 1. Install netcat  
In WSL  
	```sudo apt-get install netcat```  
To know the argument for netcat or nc you can use  
	```man netcat```  
  
## 2. Install Wireshark  
  
## 3. Setting up Wireshark  
Open Wireshark and select `Adapter for loopback traffic capture`  
In the `Apply a display filter` box type `tcp.port == 5000` because we will use port 5000 for transmitting and receiving.  
  
## 4. Setting up TCP/UDP server and client  
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
  
## 5. Checking Result on Wireshark  
If you follow all of the steps correctly, you will see 3 ways handshake and all the payloads that come with it.   
  
