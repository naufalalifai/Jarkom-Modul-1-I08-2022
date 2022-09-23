# Jarkom-Modul-1-I08-2022

## Member's Name
- Muhammad Naufal Alif Islami (05111942000008)
- Christian J H Pakpahan (5025201153)

## Content
- [Number 1](#number-1)
  - [Question](#question-)
  - [Answer](#answer-)
- [Number 2](#number-2)
  - [Question](#question--1)
  - [Answer](#answer--1)
- [Number 3](#number-3)
  - [Question](#question--2)
  - [Answer](#answer--2)
- [Number 4](#number-4)
  - [Question](#question--3)
  - [Answer](#answer--3)
- [Number 5](#number-5)
  - [Question](#question--4)
  - [Answer](#answer--4)
- [Number 6](#number-6)
  - [Question](#question--5)
  - [Answer](#answer--5)
- [Number 7](#number-7)
  - [Question](#question--6)
  - [Answer](#answer--6)
- [Number 8](#number-8)
  - [Question](#question--7)
  - [Answer](#answer--7)
- [Number 9](#number-9)
  - [Question](#question--8)
  - [Answer](#answer--8)
- [Number 10](#number-10)
  - [Question](#question--9)
  - [Answer](#answer--9)


## Number 1
### Question :
Mention the web server used on "monta.if.its.ac.id"
### Answer :
1. Display Filter 
```
http.host contains "monta.if.its.ac.id"
```
2. Right click on packet and follow HTTP stream. As you can see , Server : `nginx/1.10.3`

<img src="/pic of ans/Image 1.jpg">

## Number 2
### Question :
Ishaq was confused looking for TA topics for this semester, then he came to the monta website and found the topic details on the website “monta.if.its.ac.id”, what TA title did Ishaq open?
### Answer :
1. Display Filter 
```
http contains "detailTopik"
```
2. Right click on packet and follow HTTP stream. Get referer link `http://monta.if.its.ac.id/index.php/topik/detailTopik/194`

<img src="/pic of ans/Image 2(1).jpg">

3. Open the [LINK](http://monta.if.its.ac.id/index.php/topik/detailTopik/194) and the page will show the TA title : `Evaluasi unjuk kerja User Space Filesystem (FUSE)`

<img src="/pic of ans/Image 2(2).jpg">

## Number 3
### Question :
Filter so that wireshark only shows packets going to port 80!
### Answer :
1. Display Filter 
```
tcp.dstport == 80
```

<img src="/pic of ans/Image 3.jpg">

## Number 4
### Question :
Filter so that wireshark only picks up packets coming from port 21!
### Answer :
1. Display Filter 
```
tcp.srcport == 21
```

<img src="/pic of ans/Image 4.jpg">

## Number 5
### Question :
Filter so that wireshark only picks up packets coming from port 443!
### Answer :
1. Display Filter 
```
tcp.srcport == 443
```

<img src="/pic of ans/Image 5.jpg">

## Number 6
### Question :
Filter so that wireshark only shows packets going to lipi.go.id !
### Answer :
1. `ping lipi.go.id` in cmd to find the ip

<img src="/pic of ans/Image 6(1).jpg">

2. Display Filter 
```
 ip.dst == 203.160.128.158
```

<img src="/pic of ans/Image 6(2).jpg">

## Number 7
### Question :
Filter so that wireshark only picks up packets coming from your ip!
### Answer :
1. `ipconfig` to find my ip in cmd

<img src="/pic of ans/Image 7(1).jpg">

2. Capture Filter 
```
src host 192.168.100.66
```

<img src="/pic of ans/Image 7(2).jpg">

## Number 8
### Question :
Browse the flow of packets in the given .pcap file, look for useful information in the form of a conversation between two students regarding cheating in practicum activities. The conversation is reported to use a network protocol with a high level of reliability in its data exchange so you need to apply a filter with that protocol.
### Answer :
1. Display Filter 
```
tcp.flags.ack == 1 && tcp.flags.push == 1
```

<img src="/pic of ans/Image 8(1).jpg">

2. Found their conversation and a hint that they will make file exchanges through port 9002 

<img src="/pic of ans/Image 8(2).jpg">

## Number 9
### Question :
There are reports of file exchanges made by the two students in the conversations obtained, look for the file in question! To facilitate reporting to superiors, name the file found in the format [group_name].des3 and save the output file with the name “flag.txt”
### Answer :
1. Display Filter 
```
tcp.flags.ack == 1 && tcp.flags.push == 1 && tcp.port == 9002
```

<img src="/pic of ans/Image 9.jpg">

2. Found the salt file and save it as I08.des3
3. Execute OpenSSL command in cmd 
```
openssl des3 -d -salt -in I08.des3 -out flag.txt
```
4. The hint for the decryption password was found on their conversation and the password is `nakano`

## Number 10
### Question :
Find the secret password (flag) of the above-mentioned underground organization!
### Answer :
1. Open file flag.txt 

<img src="/pic of ans/Image 10.jpg">

2. The password is `JaRkOm2022{8uK4N_CtF_k0k_h3h3h3}`

