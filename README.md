Project 452
===========

### Introduction
This project is created for implementing TCP and UDP protocols.

### How to use?
The all parts works in the same way. There are three python files for the "part1", "part2", "part3" and "part4".

1. **relay_server.py:** This is a server.
2. **sender.py:**  This is a sender which sends "picture.jpg".
3. **receiver.py:** This is a receiver which receives "picture.jpg".

Follow the following steps to use the program:

1. Run _relay_server.py_.
2. Run _sender.py_.
3. Run _receiver.py_.

Then, output of the "relay_server.py" will be like the following:

>
**Server started to listen sender and receiver...<br>
Sender has connected: "Hello server, I am sender!"<br>
Receiver has connected: "Hello server, I am receiver!"**<br>

Enter "picture.jpg" for the "sender.py". It will be like the following:

>
**Please enter the file name you want to sent:** picture.jpg

Then, processes will be completed.

### Overview
When processes are completed, "received_picture.jpg" is created as a result for the all parts. However, size and quality of the "received_picture.jpg" differs according to protocols.

**Part 1**<br>
This is an implementation of the TCP protocol. Size of the "received_picture.jpg" is the same as "picture.jpg". Because, TCP protocol is reliable.

"picture.jpg"<br>(picture size = 384.81 kB)   | "received_picture.jpg"<br>(picture size = 384.81 kB)
--------------------------------------------- | ------------------------------------------------------
![Image](extras/1.jpg)                        | ![Image](extras/1.jpg)

As seen in the example, sizes of the "picture.jpg"  and "received_picture.jpg" are exactly the same.

**Part 2**<br>
This is an implementation of the UDP protocol. Size of the "received_picture.jpg" is usually not the same as "picture.jpg". Because, UDP protocol is not reliable. Because of packet losses, size of the "received_picture.jpg" is lower than the size of the "picture.jpg". Therefore, "received_picture.jpg" is a damaged image. 

"picture.jpg"<br>(picture size = 384.81 kB)   | "received_picture.jpg"<br>(picture size = 371.31 kB)
--------------------------------------------- | ------------------------------------------------------
![Image](extras/1.jpg)                        | ![Image](extras/2.jpg)

As seen in the example, sizes of the "picture.jpg"  and "received_picture.jpg" are not the same. Size of the "received_picture.jpg" is lower. Because some of the packets did not reach to the receiver because of unreliability of the UDP protocol.

**Part 3**<br>
This is an implementation of the "stop & wait" protocol by using UDP. This is reliable, because "stop & wait" protocol sending same packet until getting "OK" message from the receiver.

"picture.jpg"<br>(picture size = 384.81 kB)   | "received_picture.jpg"<br>(picture size = 384.81 kB)
--------------------------------------------- | ------------------------------------------------------
![Image](extras/1.jpg)                        | ![Image](extras/1.jpg)

As seen in the example, size of the sent and received pictures are exactly the same. Because reliability is provided by "stop & wait" protocol.

**Part 4**<br>
This is an implementation of the "stop & wait" protocol by using UDP. However, there is one difference from the "part3". There are "p" and "q" values between 0-1 which is taken from the "values.txt" file. "p" value represents the packet drop and error rate and "q" value represents the bit error rate. "q" is a subset of the "p" . Because if there is a bit error, it is also a packet error.

"picture.jpg"<br>(picture size = 384.81 kB)   | "received_picture.jpg"<br>(picture size = 384.81 kB)<br>(p=0.1, q=0.1)<br>   | "received_picture.jpg"<br>(picture size = 307.50 kB)<br>(p=0.3, q=0.1)
--------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------
![Image](extras/1.jpg)                        | ![Image](extras/3.jpg)                                                       | ![Image](extras/4.jpg)

As seen in the examples, there are two tries:

1. Sizes of the "picture.jpg" and the first "received_picture.jpg" are exactly the same. Because, there is no packet loss. They are calculated as the following:<br>
_**Bit error:**_ q = 0.1 = %10<br>
_**Packet error:**_ p = 0.1 = %10<br>
_**Packet drop:**_ p - q = 0.1 - 0.1 = 0 = %0<br>

2. Sizes of the "picture.jpg" and the second "received_picture.jpg" are not the same. Because, there is %20 packet loss. They are calculated as the following:<br>
_**Bit error:**_ q = 0.1 = %10<br>
_**Packet error:**_ p = 0.3 = %30<br>
_**Packet drop:**_ p - q = 0.3 - 0.1 = 0.2 = %20<br>

### License
Copyright 2019 Burak Kuyucu

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.


