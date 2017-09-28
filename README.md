# Peripherals

Peripherals live on the front side bus with other fundamental components. Plugging a peripheral in via PCIx, SCSI, or SATA physically locates that device on the system bus. Other devices like USB devices exist on a separate bus from the system bus, but are synchronized with the system bus using a USB controller and a device driver that can translate USB bus messages into system bus messages.

## Network interfaces

Independent processor caches network traffic:

[OSI model](https://en.wikipedia.org/wiki/OSI_model)

Memory address, stack pointer, data transmission rules
Processor communicates asynchronously over network connection in order to satisfy rules of protocol in use - either TCP or UDP.

IP

[Internet Protocol](https://en.wikipedia.org/wiki/Internet_Protocol)

TCP

[Transmission Control Protocol](https://en.wikipedia.org/wiki/Transmission_Control_Protocol)

UDP

[User Datagram Protocol](https://en.wikipedia.org/wiki/User_Datagram_Protocol)

#### More recommended reading

[Just2Good Description of Networking](http://www.just2good.co.uk/networking.php)

## DMA

[Direct Memory Access](https://en.wikipedia.org/wiki/Direct_memory_access)

### Hard disks

Platter-based hard disks used to be a very interesting subject of research and discussion. Imagine ultra-smooth platters spinning 100 times per second, with binary data encoded on them in sections < 100 nanometers. The hard drive is the most space age piece of equipment in your home.

You can learn about them here:
[Engineer Guy Hard Drive](https://en.wikipedia.org/wiki/File:Harddrive-engineerguy.ogv)

Platter based hard disks have an insane storage cost, less than $0.03 per gigabyte:

[BackBlaze](https://www.backblaze.com/blog/hard-drive-cost-per-gigabyte/)

SSDs are less interesting - they are just flash memory with a controller that engages your system's PCI bus.

## Cyclic Redundancy Checking

### Graphics Accelerators

Dedicated graphics pipelines - hardware designed just for manipulating pixels in an array and updating them in a shared memory used by the display. Separate pipeline from the CPU, again, graphics memory can be written to display without needing to be circled around with the CPU.

#### Shaders

C++ software (gsl, actually) that executes simple mathematics on every vertex simultaneously.

#### Pipeline components



#### Software components

OpenGL, DirectX, WebGL. CUDA, GLSL

#### Onboard memory


# Assignment:

1. The minimum seek time for an HDD is 9msec, and the maximum seek time is 90msec. The block size of this HDD is 4KB. How long on average does it take to read 100MB of data?
   *

2. Describe a TCP/IP packet in detail. Describe the header, how many bytes it is, and which components it contains. What data can come after the header?
   * The TCP/IP packet is used in communication between mediums. TCP is know for assuring packets get where they are intended. TCP packets are sent in an unstructured manner and are assembled in order by the receiving medium. The headers in the packets are the following.
    1. Source port and Destination port
       * These identify the end points of the connection.
    2. Sequence Number
       * Is the number given to to the first byte of the current packet. The the number is used to keep the session alive and to keep track of the number of bytes that have been transmitted.
    3. Acknowledgement number
       * The ack number is closely related to the syn number. The ack number has  the same mechanism as the syn and both are used to keep track of bytes sent and are also used to determine packet loss.
    4. Data offset
       * This field contains a number used to determine where the header ends and where the data starts. For ex. a 120 byte packet can have an offset of 5 which you multiply by 4 (bytes) which gives you 20 then the header is 20 bytes and the data is 100 bytes.
    5. Reserved
       * It is used to make sure the data offset field can be expressed in multiples of 4 (to represent bytes). The value of this field is 0 always.
    6. Flags
       * Used to add certain flags
        * URG - indicates the data is Urgent
        * ACK - indicates the ACK number is valid
        * PSH - indicates the data should be passed to the application as soon as possible
        * RST - resets the connection
        * SYN - synchronizes sequence number to initiate the connection
        * FIN - means the sender has finished data transmission
    7. Window size
       * It determines the size of the senders receive window. The field pretty much tell the sender i can only receive x amount of data so don't send me more. This field can be set to handle data flow. At times the receiver will set the window size to 0 because it is overwhelmed with data but will change the field once it is ready to handle more data
    8. Checksum
       * This field is used to check id the header was damaged/incomplete while in transit to the destination.
    9. Urgent pointer
       * point to the first urgent data byte in the packet. When this field is set the stack receiving the packet automatically stops all that is doing to deliver this packet.
    10. Options
        * Is used to set various TCP option that are not required

3. How does the network protocol guarantee that a TCP/IP packet is complete after transmission?
   * TCP has error checking. It use syn/ack headers to check if all the data has been received by the end point. If at one point the endpoint sees a discrepancy in the data it will request the packet to be sent again.

4. What is the difference between TCP and IP?
   * TCP is the protocol in charge of data delivery. IP is the protocol in charge of addressing. IP is used to configure endpoint with routing and switching in order to establish a gateway to other endpoints. In simpler terms IP gives an address and TCP makes sure it gets there.

5. Why is 3d performance so much higher with a graphics card than without? Modern CPUs are extremely fast, what is limiting their performance?
   * 3D performance is much higher with a GPU because they are fined tuned to calculate mathematical sequences at a very fast pace. Most of the stuff a GPU has to do revolves around mathematics so they made them to be very efficient. Also, GPU can execute much more 32 bit instruction per clock cycle than CPUs.
   * CPU performance is limited because the cpu has to handle running the whole pc. THE CPU must determine how to allocate resources to different task like saving a pdf, running chrome, opening atom, etc. In being in charge of all of that the CPU can't just focus on graphics. While a GPU mainly worries in graphics and can allocate all of its power at doing the best it can.
