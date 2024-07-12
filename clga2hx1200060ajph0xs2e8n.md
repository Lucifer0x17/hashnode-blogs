---
title: "How Your Request Converted to Binary bits?"
datePublished: Mon Apr 10 2023 00:00:20 GMT+0000 (Coordinated Universal Time)
cuid: clga2hx1200060ajph0xs2e8n
slug: osi-model
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1681076224155/4c3b16b2-e5df-4100-94c1-cd784ee25328.jpeg
tags: backend, osi, backend-development, model-osi, protocols

---

---

Hey, I am Lucifer. I am a backend developer and a very curious person and I like to learn new things about tech. I started learning about the fundamentals of Backend development and started digging into Communication Protocols. As we all know devices only understand 0s and 1s and our data transmits into bits but we never write that. So, How does the request to `www.google.com` convert to 0s and 1s and reaches Google's server?

The answer is **OSI Model** also known as **Open System Interconnection Model.** The OSI model is a framework for data communication over a network, consisting of seven layers each with specific roles and protocols. It starts with the Physical Layer dealing with physical aspects and goes up to the Application Layer providing a wide range of protocols and services for data exchange. If you want to know more about the layers you can check out the following tweet.

%[https://twitter.com/Lucifer0x17/status/1645182532990672898] 

So, with all these 7 layers they usually work in reverse order from a user perspective. As a user uses a browser to ping Google the request goes from Layer 7 to Layer 1.

### What happens at Layer 7?

Let's say your device's IP and MAC are 10.0.0.5 and ABC respectively and Google's server's IP and MAC are 8.8.8.8 and XYZ. So, when you ping google.com you are sending a GET/ request from 10.0.0.5 to 8.8.8.8 so the job of layer one is to prepare all of the raw materials just like a chef's assistant. The Application Layer creates a string on request, headers including cookies, content-type etc. This is where the job of Layer 7 is done and it passes that string to Layer 6.

> Note: We are overseeing the public and private IP and also, the DNSSEC.

### Is it all gibberish now?

The Presentation Layer or Layer 6 takes that string and converts it into whatever data type is defined in the content-type and then compresses it if needed. If the request is HTTP then this layer's work is done but nowadays all the requests are HTTPS, so here at Layer 6 the encryption happens.

And for the example let's assume the whole string of our GET/ request gets converted to ELGOOG. Now, it's time for Layer 5 to shine.

### You belong with me

Google has open servers and anyone can send requests to that server, right? Even you can send two requests from two different browsers. So, to keep that in check SessionLayer or Layer 5 comes to the rescue.

Layer 5 adds an id known as session id to the encrypted request (gibberish for humans) to map it to a particular application of that IP. I.e. now our ELGOOG becomes IDELGOOG and it will be treated as the whole request for the later layers.

### We are breaking stuff now

Transport Layer or Layer 4's job is to make the bunch of bytes ready to ship, here, IDELGOOG. If you think about it, it's hard to ship large things right, so, the transport layer breaks the whole thing into smaller portions known as Segments.

Ex: IDE, LGO and OG. Each segment is then tagged with a lot of information but for simplicity, it's tagged with the port number. Every application runs on a specific port on a device so we will consider our browser is running on port 123 and Google is listening at port 80.

After implementing that our segments will look like 123IDE80, 123LGO80 and 123OG80. We need the source port because when Google responds it should know where to go to. So now our requests are ready to be shipped.

### Or not

We have packed all our stuff to ship but there is still one thing missing. The source and destination addresses. So, here we add the street name and other info. The Network Layer or Layer 3 adds the source and destination IP addresses to the segments along with some other information. The source address is added for two reasons: to get the response and to revert if something happens and the request doesn't reach the destination.

After passing through Layer 3 our segments will be 10.0.0.5123IDE808.8.8.8, 10.0.0.5123LGO808.8.8.8 and 10.0.0.5123OG808.8.8.8 These upgraded segments are known as Packets.

### Confusing or Interesting?

The packets are ready and can reach your streets but still, they can't reach you. They require your house number. And in the world of computers, every device has a unique number known as MAC address. The Data Link layer or Layer 2 adds the MAC addresses to the packets but before I explain that we can see that packets are already bigger so we will divide and conquer.

But here the division takes place a little differently, first, all the packets are merged one after another and then get broken into smaller portions called frames. In our case, it will be like 10.0.0.5123IDE808.8.8.810.0.0.5123LGO808.8.8.810.0.0.5123OG808.8.8.8 and then to 10.0.0., 5123IDE, 808.8.8, .810.0., 0.5123L, GO808.8, .8.810., 0.0.512, 3OG808., 8.8.8

Now the MAC address is added to each of these portions which are then called frames. ABC10.0.0.XYZ, ABC5123IDEXYZ, ABC808.8.8XYZ, ABC.810.0.XYZ, ABC0.5123LXYZ, ABCGO808.8XYZ, ABC.8.810.XYZ, ABC0.0.512XYZ, ABC3OG808.XYZ, ABC8.8.8XYZ

> Note: The frames don't need to be of equal sizes. Also, nowadays ARP is used to add the MAC

### Back to the Real World

All the frames are now passed to the Physical Layer or Layer 1 and here all the magic happens. Physical layers are the wires which connect all the devices on the internet. Someone made it possible to transmit 0s and 1s through electricity and because of that, we can share all the pieces of information.

So, in Layer 1 all those frames get translated to 0s and 1s through digital encodings and fed to wires to be shipped. We will talk about encoding in another blog as It's already a long blog.

### Now it all makes sense!

This is it for now. I got my aha! moment when I understood how things work under the hood. Hope you also have that moment too. Will write soon.

Happy Programming :)