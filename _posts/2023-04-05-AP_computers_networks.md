---
toc: true
comments: true
layout: post
title: Computers and Networks (Unit 4)
categories: []
---

## Requirements
> Work through College Board Unit 4... blog, add definitions, and pictures.  Be creative, for instance make a story of Computing and Networks that is related to your PBL experiences this year.


### How a Computer Works
> As we have learned, a computer needs aa program to do something smart.  The sequence of a program initiates a series of actions with the computers Central Processing Unit (CPU). This component is essentially a binary machine focussing on program instructions provided.  The CPU retrieives and stores the data it acts upon in Random Access Memory (RAM). Between the CPU, RAM, and Storage Devices a computer can work with many programs and large amounts of data.

List specification of your Computer, or Computers if working as Pair/Trio
- Processor GHz: Processor Intel(R) Core(TM) i7-3517U CPU @ 1.90GHz, 2401 Mhz, 2 Core(s), 4 Logical Processor(s)
- Memory in GB: 8.00 GB
- Storage in GB: 143 GB
- OS: 22621.1555 Windows 11

Define or describe usage of Computer using Computer Programs. Pictures are preferred over a lot of text.  Use your experience.
- Input devices
- Output devices
- Program File
- Program Code
- Processes
- Ports
- Data File
- Inspect Running Code
- Inspect Variables


![Computer Hardware]({{site.baseurl}}/images/cpu.jpeg)


### The Internet
> Watch/review College Board Daily Video for 4.1.1

- Essential Knowledge
    - A computing device is a physical artifact that can run a program. Some examples include computers, tablets, servers, routers, and smart sensors.
    - A computing system is a group of computing devices and programs working together for a common purpose.
    - A computer network is a group of interconnected computing devices capable of sending or receiving data.
    - A computer network is a type of computing system. 
    - A path between two computing devices on a computer network (a sender and a receiver) is a sequence of directly connected computing devices that begins at the sender and ends at the receiver.
    - Routing is the process of finding a path from sender to receiver.
    - The bandwidth of a computer network is the maximum amount of data that can be sent in a fixed amount of time.
    - Bandwidth is usually measured in bits per second

- Complete Vocabulary Matching Activity.  Incorporate this into your learnings from year.  To analyze measure path and latency use `traceroute` and `ping` commands from Linux Terminal.  
    - Path 
    - Route
    - Computer System
    - Computer Device
    - Bandwidth
    - Computer Network

> Watch/review College Board Daily Video 4.1.2

- Complete True of False Questions

- Essential Knowledge
    - The internet is a computer network consisting of interconnected networks that use standardized, open (nonproprierary) communication protocols.
    - Access to the internet depends on the ability to connect a computing device to an internet connected device.
    - A protocol is an agreed-upon set of rules that specify the behavior of a system.
    - The protocols used in the internet are open, which allows users to easily connect additional computing devices to the internet.
    - Routing on the internet is usually dynamic; it is not specified in advance
    - The scalability of a system is the capacity for the system to change in size and scale to meet new demands.
    - The internet was designed to be scalable
    - Information is passed through the internet as a data stream. Data streams contain chunks of data, which are encapsulated in packets. 
    - Packets contain a chunk of data and metadata used for routing the packet between the origin and the destination on the internet, as well as for data reassembly.
    - Packets may arrive at the destination in order, out of order, or not at all
    - IP, TCP and UDP are common protocols used on the internet.
    - The world wide web is a system of linked pages, programs, and files.
    - HTTP is a protocol used by the world wide web
    - The world wide web uses the internet

- Go over AP videos, vocabulary, and essential knowledge.  Draw a diagram showing the internet and its many levels. A preferred diagram would using your knowledge of frontend, backend, deployment, etc.  Picture would highligh vocabulary by illustration. The below illustration have some ideas

![Full Stack]({{site.baseurl}}/images/fullstack.png)


- Often we draw pictures of machines communicating over the Internet with arrows.  However, the real communication goes through protocol layers and the machine and then is trasported of the network.   For College Board and future Computer Knowledge you should become familiar with the following ...

```
     User Machine  <---> Frontend Server <---> Backend Server
    +-----------+         +-----------+         +-----------+
    |  Browser  |         |  GH Page  |         |   Flask   |
    +-----------+    ^    +-----------+    ^    +-----------+
    |    HTTP   |    |    |    HTTP   |    |    |    HTTP   |
    +-----------+    |    +-----------+    |    +-----------+
    |    TCP    |    |    |    TCP    |    |    |    TCP    |   
    +-----------+    |    +-----------+    |    +-----------+
    |     IP    |    V    |     IP    |    V    |     IP    |
    +-----------+         +-----------+         +-----------+
    |  Network  |  <--->  |  Network  |  <--->  |  Network  |
    +-----------+         +-----------+         +-----------+
```

The "http" layer is an application layer protocol in the TCP/IP stack, used for ***communication between web browsers and web servers***. It is the protocol used for transmitting data over the World Wide Web.

The "transport" layer (TCP) is responsible for providing reliable data transfer between applications running on different hosts.  The TCP protocol segments the data into smaller ***chunks called "segments"***. Each segment contains a sequence number that identifies its position in the original stream of data, as well as other control information such as source and destination port numbers, and checksums for error detection.

The "ip" layer is responsible for packetizing data received from the TCP layer of the protocol stack, and then ***encapsulating the data into IP packets***. The IP packets are then sent to the lower layers of the protocol stack for transmission over the network.

The "network" layer is responsible for ***routing data packets between networks*** using the Internet Protocol (IP). This layer handles tasks such as packet addressing and routing, fragmentation and reassembly, and ***network congestion*** control.


### Fault Tolerance
> Watch both Daily videos for 4.2

- Complete the network activity, summarize your understanding of fault tolerance.


### Parallel and Distributed Computing
> Review previous lecture on Parallel Computing and watch Daily vidoe 4.3.  Think of ways to make something in you team project to utilize Cores more effectively.  Here are some thoughts to add to your story of Computers and Networks...

- What is naturally Distributed in Frontend/Backend archeticture?  

- Analyze this command in Docker: ```ENV GUNICORN_CMD_ARGS="--workers=1 --bind=0.0.0.0:8086"```.   Determine if there is options are options in this command for parallel computing within the server that runs python/gunicorn.  Here is an [article](https://medium.com/building-the-system/gunicorn-3-means-of-concurrency-efbb547674b7)


> Last week we discussed parallel computing on local machine.  There are many options.  Here is something to get parallel computing work with a tool called Ray.
- Review this [article](https://www.anyscale.com/blog/writing-your-first-distributed-python-application-with-ray)...  Can you get parallel code on images to work more effectively?  I have not tried Ray.

- Code example from ChatGPT using squares.  This might be more interesting if nums we generated to be a lot bigger.

```python
import ray

# define a simple function that takes a number and returns its square
def square(x):
    return x * x

# initialize Ray
ray.init()

# create a remote function that squares a list of numbers in parallel
@ray.remote
def square_list(nums):
    return [square(num) for num in nums]

# define a list of numbers to square
nums = [1, 2, 3, 4, 5]

# split the list into two parts
split_idx = len(nums) // 2
part1, part2 = nums[:split_idx], nums[split_idx:]

# call the remote function in parallel on the two parts
part1_result = square_list.remote(part1)
part2_result = square_list.remote(part2)

# get the results and combine them
result = ray.get(part1_result) + ray.get(part2_result)

# print the result
print(result)

```

## College Board Daily Video 4.1.2

The internet is computer network consisting of interconnected networks that use standardized, open communication protocols. Access to the interenet depends on the ability to connect a computing device to an internet connected device. 
- A protocol is an agreed-upon set of rules that specify the behavior of a system. 
- The protocols used in the Internet are open, which allows users to easily connect additional computing devices to the internet
- Routing on the internet is usually dynamic; it is not specified in advance

The scalability of a system is the capacity for the system to change in size and scale to meet new demands. The internet was designed to be scalable. 

A packet is a small amount of data sent over a network. Each packet also includes the source and the destination information. A protocol is an agreed-upon set of rules that specify the behavior of a system. 

#### Computer Protocol Models
1. OSI - Open Systems Interconnect
> The layers you have to go through to communicate. The 7 group of protocols are Physical, Data Link, Network, Transport, Session, Presentation, Application. 

2. IETF - Internet Engineering Task Force
> Manages the development of standards and technical discussions concerning the internet in an open and collaborative process. 

3. TCP - Transmission Control Protocol 
> Establishes a common standard for how to send messages between devices on the internet. 

There are many different protocols, standards, data formats, etc. Used at the "Application" and "Transport" layers. There are many different protocols and hardware used at the Network Access Layer. Ethernet, WIFI, Cable, Fiber Optics. They meet in the middle at the "Internet" layer where you use Internet Protocol Addresses. IP Adressing is the common link, and relatively simple. 

Internet Engineering Task Force (IETF) - Manages the development of internet standards via written techinical discussions in an open and collaborative process. 

#### Network Access Layer
- Putting and pulling the 1's and 0's from a wire or radio wave. This layer is focused on the hardware and protocols that carry 0's and 1's between two devices. 

The most common Network Access Protocol is Ethernet, implemented in Network Interface Cards (NIC). A general function of the physical layer is to deliver packets from one NIC to another. This is reffered to as a "hop". 
- Each NIC has a unique address associated with it called a Media Access Control (MAC) Address. It is used for local hops.
> Data Link, Fiber, MAC, Ethernet, NIC, Wire

#### Network Access/Internet Layer Data Transmission 
A packet contains data that is being transmitted as well as metadata containing information used for routing information. 

Internet Layer - The internet was designed to be scalable-able to change in size and scale to meet new demands. 

#### The Scalability of the Internet 
Local Area Network (LAN) - Physical connections limited by hardware and physics. 

Autonomous Systems (AS) - Large intranets linked together under the control and policies of major organizations. Large routers link networks with large telecommunications connections

The Internet - Autonomous Systems (AS) Linked Together as large routers linking via Telecom Means (Fiber, T3, Satellites) or Major Infrastructure - DNS (.com, .net, .etc), Cyber Operations

#### Transport Layer
Open standards and protocols enable different manufactures and develoers to build hardware and software that can communicate with hardware and software on the rest of the internet. 
- Different Types of Protocols
    - TCP does error checking and error recovery so it is slower
        > Slower but reliable, Three-way Handshake, Typical Applications are Email and Web-browsing.
    - UDP performs error checking, but it discards erroneous packets. 
        > Fast but does not guarantee transfers, best effort, Typical Applications are Music Streaming and VolP

### Review

1. Open standards and protocols enable different manufactureres and developers to build hardware and software that can communicate with hardware and software on the rest of the internet
> True

2. IETF is a task force used to enforce laws to keep manufacturers out of the internet
> False

3. Routes are determined in advanced and are not flexible.
> False

4. A protocol is an agreed-upon set of rules that specify the behavior of a system
> True 

5. UDP guarantees transfers and is faster.
> False

6. The World Wide Web is the internet
> False 

7. HTTP is a protocol used by the World Wide Web. 
> True
