---
title: "The mode of travel of Bits in Internet"
seoDescription: "A brief summary of my understanding of the internet protocols to traverse the data through Internet.
Is Web Sockets and Sockets are same?"
datePublished: Sun Apr 30 2023 21:19:56 GMT+0000 (Coordinated Universal Time)
cuid: clh3x0jc7000f09ml8ec14zkv
slug: tcp-udp-https
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1682884200132/7a64c429-282e-4fa0-88a9-99ebad718728.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1682889433622/18cc1870-c541-4bb7-a00f-74986c3c034d.jpeg
tags: websockets, socket, tcp, udp, ip

---

---

Hey, I am Lucifer. I am a backend developer and a very curious person and I like to learn new things about tech. I started learning about the fundamentals of Backend development and started digging into Communication and Networking. In my [previous blog](https://hashnode.lucifer0x17.dev/osi-model), I talked about the OSI model, where we learned about how a simple request is converted to bits.

If you think about one thing you will realize that at the Transport layer and Application layer we are sending a lot of data, but data should be understandable by the receiver end too. Else, it's no point in going through the seven layers if the data is not received and compiled correctly. For this, there exists a concept known as Network Protocols and they exist in Transport Layer (`TCP/IP, UDP`) and Application Layer (`HTTPS, FTP, SMTP, SNMP, etc.`) and have different use cases.

### Do we even need this?

To answer in a word Yes, we do need these protocols for a different number of reasons that we will discuss shortly.

* Let's talk about the Trasport Layer protocols first as they were invented a lot before application layer protocols. We need these protocols as they are the ones that help the bits to reach the destination and also, depending on the requirement of the connection between two parties either TCP/IP or UDP/IP is used.
    
* Before the browsers and applications were made things used to work till layer 4 only and usually a string is used to transfer from the sender to the receiver. Though as technology advances it became hard to just stick to these transport layer protocols as there is no handling of sessions and encryption of data and also it was only meant for transport layer programs.
    
    %[https://www.youtube.com/watch?v=qqRYkcta6IE&t=2153s] 
    
* Then some amazing people came up with different Application Layer Protocols with respective needs. Different protocols were introduced based on the requirements. SMTP (`Simple Mail Transfer Protocol`) was introduced as the name suggests to send emails. FTP (`File Transfer Protocol`) helped to transfer files and many more. [Here](https://www.geeksforgeeks.org/protocols-application-layer/), is a good article to learn about main application layer protocols.
    
* After these Application layer protocols, in 1996, HTTP (`Hyper Text Transfer Protocol`) was introduced which gives us client-server architecture and it revolutionize the internet. It is also an Application layer protocol that works over TCP/IP. However, Google launched HTTP over QUIC which uses UDP/IP under the hood. You can refer to this [article](https://cs.fyi/guide/http-in-depth) to learn more about HTTP as it is in itself a very big topic.
    
    %[https://www.youtube.com/watch?v=0OrmKCB0UrQ&t=615s] 
    

### Are Web Sockets and Sockets same?

The whole research that I shared above started with this question only. As I always get confused between WebSocket and `socket.on()` function while creating a simple web server over TCP/UDP. As, `socket.on()` never shows the functionality of Web Sockets even though they share the same name.

The sockets in the web server stand for the three things which help to determine the network connection whereas the Web Socket is a full-duplex (`data can be transmitted in both directions on a signal carrier at the same time`) communication channel built using the TCP sockets. The Sockets have three data that help to determine a connection and are:  
\- Type of connection (`TCP/UDP`)  
\- IP address  
\- Port Number

### It's time to pen down

I know there are a lot of things that can be added to the blog and I have not explained it thoroughly. The reason is that there are already a lot of people who have explained those things already and in a better way.

I wrote this blog to answer the questions which came to my mind very often and gave me a lot of trouble in finding the answers. I got my answers after a thorough research and hoping that some of your questions have been answered too after reading this blog. Will write soon.

Do share your thoughts in the comment and let me know if I missed something.

Happy Programming :)