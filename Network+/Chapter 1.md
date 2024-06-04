# What is a Network
- A <font color="#ff0000">Network</font> is two or more connected computers that can share resources such as data, applications, machines, Internet connections. They communicate using Binary.
- LAN
	- <font color="#ff0000">Local Area Network</font> is physically connected devices that are in close proximity to each other. Normally connected to via a <font color="#ffc000">hub</font> or a <font color="#ffc000">switch</font> physically.
	- Try to put LAN's into <font color="#ffc000">Work-groups</font> such as Marketing or Sales.
		- This is for the purpose of easier Administration.
	
> [!NOTE] Logical Vs. Physical
> - Logical is when some device is noting logically where a device connects to another instead of actually being connected physically.
> 	- Its like If I wrote on a piece of paper where my Home is but I my not be physically at my home yet. That is what <font color="#ffc000">Routers</font> are for.

# Work Station Vs. Server Vs. Hosts Vs. Client Machines

> [!attention] About Name Convention
> Host, Workstation, and Client are all used interchangeably by most people to refer to the same thing so be sure to be careful technically.

- <font color="#ff0000">Workstation</font>:
	- Power PC with more than one CPU
	- Resources are available to others on the network
> [!NOTE]
> Workstations are not as powerful as a Server and they are not a client computer or personal computer but could be technically.
- <font color="#ff0000">Server</font>:
	 - Very Powerful Computers that are "at the service" to the network and generally do <font color="#ffc000">one specific task</font> but can do many tasks if you wanted to.
	 - They Run on whats called a <font color="#ffc000">network operating system</font>.
	 - They give resources to a ton of client machines
	 ## Common Types of Servers
	- <font color="#ffc000">File Server</font>: Stores and Deletes Files
	- <font color="#ffc000">Mail Server</font>: Email Functions
	- <font color="#ffc000">Print Server</font>: Manages Printers
	- <font color="#ffc000">Web Server</font>: Utilities HTTPS for storing web content and pages
	- <font color="#ffc000">Fax Server</font>: Sends and Receives paperless faxes
	- <font color="#ffc000">Application Server</font>: Network Applications
	- <font color="#ffc000">Telephony Server</font>: Call center, Routing calls
	- <font color="#ffc000">Proxy Server</font>: Handles misc tasks in place of of other machines
- <font color="#ff0000">Hosts</font>:
	- Any network devices such as workstations and servers that have an IP address.
- <font color="#ff0000">Client Machine</font>:
	- Any Device that can ask for access to resources from things like a printer, server, or powerful workstation.
# Network Types
- <font color="#ff0000">MAN</font>
	- Metropolitan Area Network: used for large areas such as buildings in cities or connecting different facilities for different purposes.
		- This normally happens using a carrier provider such as Verizon where they lease a line to your building to provide internet and then can take it away at will.
		- Smaller concentrated 
- <font color="#ff0000">WAN</font>^balls
	- Wide Area Network: Span large geographical areas and use some type of router and public links to access.  The internet is a WAN!
		- WAN's can use public and private data transport media/wires such as phone lines to get data across.
		- WAN's are by definition a <font color="#ffc000">internetwork</font> of computers or internet!
			- Specifically a <font color="#ffc000">distributed WAN</font> since devices connect to each other from all around the world.
			- There is also <font color="#ffc000">centralized WAN's</font> where there is a central computer or location where all devices connect.

> [!example] Centralized WAN Example
> remote offices around the world connecting to main corporate office.
- <font color="#ff0000">PAN</font>
	- Personal Area Networks: Close Proximity Devices connecting such as Bluetooth headphones to the phone which may connected physically to the PC.
- <font color="#ff0000">CAN</font> 
	- Campus Area Network: limited geographical network such as college campus or corporate campus.
	- Larger than a LAN but smaller than a MAN and a WAN.
- <font color="#ff0000">SAN</font>
	- Storage Area Network: interconnect servers to storage arrays with centralized hard drive and storage media space.
		- The protocols for a SAN are designed for storage with <font color="#ffc000">Fibre Channel</font> being the most common older tech and <font color="#ffc000">iSCSI</font> being the newer better protocols.
			- <font color="#ffc000">FCoE</font> (Fibre Channel over Ethernet) is used to encapsulate Fibre Channel into the Ethernet to still use iSCSI technology.
		- The network Hardware is also different for SANs.
- <font color="#ff0000">SDWAN</font>
	- Software Defined Wide Area Network: <font color="#ffc000">virtual WAN</font> that uses software to manage devices and services to make changes in the network.
		- It gets around hardware issues and can dynamically easily handle error management better.
		- Uses any type of <font color="#ffc000">Transport architectures</font> such as <font color="#ffc000">MPLS</font>, <font color="#ffc000">LTE</font>, and <font color="#ffc000">Broad-Band</font> internet serves.
	- <font color="#ff0000">MPLS</font>
		- Multi-Protocol Label Switching: Super popular WAN protocol which is a switching mechanism that puts labels on data and uses the label to forward the data where it needs to go in a network.
			- <font color="#ffc000">Labeling</font> is done by the routers on the edge of the network
			- <font color="#ffc000">Forwarding</font> is done inside the cloud via MPLS.
		- Pros: The Physical layout is flexible since it routes through the cloud
			- Data is the priority
			- Huge redundancy
			- one to many logical connections
- <font color="#ff0000">mGRE</font>
	- Multi-Point Generic Routing Encapsulation: a protocol given via a service provider that can dynamically terminate and create connections or tunnels to a given node.
		- A node is like a router which connects to many another devices. The mGRE protocol would allow for just one direct communication to all those devices over one tunnel.
		- Used in Dynamic Multi-point VPN deployments.
# Network Architecture
- <font color="#ff0000">Pear-to-Pear</font>
	- When the client computers are connected to each other via either a switch or router and they just share each others resources directly to one another.
		- It on each of the client machines to handle security of its own resources and for them to back up the data on that specific machine since it might be different on the other local machines.
- <font color="#ff0000">Client-Server</font>
	- When a server handles all the security and choice of forwarding to where resources are within the network. This includes logging into the client machine.
		- The server tests your access and then will tell the router where to route you for the actual information such as passwords in the <font color="#ffc000">active directory</font>.
# Physical Network Typologies

> [!NOTE] Physical vs Logical Typologies
> - The physical typologies give you the lay of the land and the cables
> - The Logical typologies are the ones that give you how a digital signal moves around the network.


--- start-multi-column: ID_rcnx
```column-settings
Number of Columns: 2
Largest Column: standard
Border: off
```

- <font color="#ff0000">Bus Topology</font>:
	- A single line of Ethernet cable in which each device connects to the line via drop cables and some kind of connector.
	- <font color="#ffc000">Drop Cables</font> are the cable that connects the Main wire to the NIC of the Device.
		- Connector types include T, RJ-45, BNC.
	- Everyone can see the data on the wire but only the destination device gets the data.
	- <u>Pros</u>: Easy install, inexpensive.
	- <u>Cons</u>: Hard to Troubleshoot, change, and move....<font color="#ffc000">Fault Tolerance</font> in the main cable is low.

--- column-break ---

![Bus Topology Image](attachments/Bus%20Topology%20Image.png)

--- end-multi-column

--- start-multi-column: ID_xzym
```column-settings
Number of Columns: 2
Largest Column: standard
Border: off
```

- <font color="#ff0000">Star Topology</font> (Hub-and-spoke):
	- Centralized switch  or hub which handles all the connections of each device.
	- <u>Pros</u>: Fault Tolerant, easily expandable, easy to troublshoot.
	- <u>Cons</u>: Larger Cost due to more cables, single point of failure due to hub or switch.
	
> [!NOTE] Point-to-Point Star Topology & Wireless Access point Topology
> - These are 2 other advanced versions of the star topology which use another switch to which connects to the other central switch to extend the network for a <font color="#ffc000">point-to-point</font> contact.
> - The <font color="#ffc000">Wireless Access Point Topology</font> uses a <font color="#ffc000">Access point</font> as its central switching device and is the wireless counter part to the switch/hub.


--- column-break ---

![Star Topology switch](attachments/Star%20Topology%20switch.png)

![Star Topology access point](attachments/Star%20Topology%20access%20point.png)

--- end-multi-column

--- start-multi-column: ID_znb5
```column-settings
Number of Columns: 2
Largest Column: standard
Border: off
```

- <font color="#ff0000">Ring Topology</font>:
	- Each computer is connected to another computer in circle or ring.
	- Pros: No need for extra network devices such as switch or router.
	- Cons: Non-fault tolerant, hard to add devices, expensive because of cables, hard to manage.
	
> [!Important] LAN Vs. WAN use
> It is almost never used in LAN environments, but is used in WAN for technology such as <font color="#ffc000">SONET</font>!

--- column-break ---

![Ring Topology](attachments/Ring%20Topology.png)

--- end-multi-column

--- start-multi-column: ID_0fiq
```column-settings
Number of Columns: 2
Largest Column: standard
Border: off
```

- <font color="#ff0000">Mesh Topology</font>:
	- It is when every single computer is connected to every other computer. Well every node at least, so mainly the switches are interconnected which are then connected to the computers.
		- Some nodes have extra wires for even more redundancy.
	- <font color="#ffc000">Partial Mesh Topology</font>: When only some nodes are fully connected and some are left to a lower tolerance. This saves some money and management!
	- <font color="#ffc000">Hybrid Mesh Topology</font>: Some parts are mesh and some are a simper topology which is what is mostly implemented today.
	- <u>Pros</u>: Max Fault Tolerance
	- <u>Cons</u>: Super Pricey, hard to manage, increases in difficulty the more computers you have.

--- column-break ---

![full Mesh Topology](attachments/full%20Mesh%20Topology.png)

> [!attention] Important!
> It is only a full on mesh topology if every singe device is connected to all other devices!

> [!Mathy]
> For <font color="#ff0000">n</font> hosts there are this many connections: <font color="#ff0000">$\frac{n(n-1)}{2}$</font>

--- end-multi-column

--- start-multi-column: ID_fter
```column-settings
Number of Columns: 2
Largest Column: standard
Border: off
```

- <font color="#ff0000">Point-To-Point Topology</font>:
	- When there is a direct communication between two routers or switches or devices via a physical cable or a logical circuit such as <font color="#ffc000">frame relays</font> or <font color="#ffc000">MPLS</font>
		- Routers are linked via a <font color="#ffc000">T1 Serial Cable</font>!
		- <font color="#ffc000">Lighting bolts</font> cable represents a WAN link or serial link.
		- <font color="#ffc000">Solid Line cable</font> represents a direct Ethernet link.

--- column-break ---

![PointToPoint Serial Wires](attachments/PointToPoint%20Serial%20Wires.png)

--- end-multi-column

--- start-multi-column: ID_v98l
```column-settings
Number of Columns: 2
Largest Column: standard
Border: off
```

- <font color="#ff0000">Point-To-Multipoint</font>:
	- When one device goes to many devices such as one router to many routers.

--- column-break ---

![PointToMultipoint topology](attachments/PointToMultipoint%20topology.png)

--- end-multi-column

--- start-multi-column: ID_usri
```column-settings
Number of Columns: 2
Largest Column: standard
Border: off
```

- <font color="#ff0000">Hybrid Topology</font>:
	- When multiple network typologies are used within a network.

--- column-break ---

![Mesh Topology](attachments/Mesh%20Topology.png)

--- end-multi-column

# Topology Selection
- Things to note when making the correct selection:
	- Cost, Ease of Installation, Ease of Maintenance, Fault-Tolerance requirement, Security requirement.
	- The cost of a large number of quality cables can be more expensive than network devices such as switches or routers.
# Network Backbone
- The strong wired connection of cables behind the switches and that connect all the segments of a network.
	- Normally uses <font color="#ffc000">Gigabit Ethernet</font> to connect to switches and directly to Servers.
# Network Segments
- The devices that make up a small section of the network that is not the backbone. 
- The servers may be in one segment. The Devices connected in front of a switch might be another segment.
# Service-Related Entry Points
- The boundary between a customers LAN and where the customer connects to the ISP's WAN.
	- Usually connected to <font color="#ffc000">smart jack</font> which is used to run diagnostics on the ISP end, up to the point of your LAN.
	- The term for the boundary is <font color="#ffc000">demarcation point</font> or <font color="#ffc000">demarc point</font> which is the line of responsibility for the ISP.
# Service Provider Links
- Telephone companies have copper connections to homes to use <font color="#ff0000">DSL</font> (Digital Subscriber Lines) which provides internet and was a good alternative to <font color="#ffc000">cable</font> or <font color="#ffc000">fiber</font>.
- Cable companies now offer data and internet services over <font color="#ffc000">hybrid fiber/coax</font> on top of there normal cable TV offerings. This uses a modem at the customers house.
- There are also <font color="#ffc000">Leased Lines</font> which is when a provider installs a direct connection between the provider and customer which is private using copper or fiber.
	- This provides no sharing of bandwidth and is a secure private connection.

# Virtual Networking
- To eliminate the need for external hardware networking devices, you can virtualize the devices onto a server.
	- Example of this is the <font color="#ffc000">vSwitch</font> technology by VMware which makes a <font color="#ffc000">virtual network device</font> such as a switch or router.
		- For the device to do networking functions, it needs a <font color="#ff0000">NIC</font> so a <font color="#ff0000">vNIC</font> (virtual Network Interface Card) needs to be installed so the virtual device connects to the hypervisor and then from there to the LAN.
		- This is done via the <font color="#ff0000">Hypervisor</font> which allows for multiple VM's to be connected to a single bare metal server at the same time and use its resources.
- The process that vSwitch does is called <font color="#ff0000">NFV</font> (Network Function virtualization) which is the process  of virtualizing the function of different networking devices to run on a single device.

# Three-Tiered Model & Collapsed-Core Model

--- start-multi-column: ID_d3vd
```column-settings
Number of Columns: 2
Largest Column: standard
Border: off
```

- A model that consists of a Core layer, Distribution layer, and an Access layer which is used to represent the general structure of most networks.
	- <font color="#ff0000">Core Layer</font>:
		- <font color="#ffc000">Backbone of the network</font> where WAN lines are placed to connect the large different area of a network such as across geographical regions. 
		- This layer is <font color="#ffc000">high availability</font> and does routing and switching and should be very fast.
	- <font color="#ff0000">Distribution Layer</font>: 
		- This layer is a ton of routing the connections from the core layer to the access layer switches.
			- This is where <font color="#ffc000">packet filtering</font>, <font color="#ffc000">security policies</font>, <font color="#ffc000">VLAN routing</font>, and defining broadcast domains happens.
	- <font color="#ff0000">Access Layer</font>:
		- <font color="#ffc000">edge switching</font> to host computers.
		- this is were access to the internet occurs, <font color="#ffc000">Quality service</font>(Qos), and <font color="#ffc000">power over Ethernet</font>(PoE) and security.
- <font color="#ff0000">The Collapsed-Core Model</font> is the newer and simpler version of the Three-Tiered Model which just has the Core and Distribution layer as one layer since our <font color="#ffc000">modern day switches</font> can handle both functions in one set of devices.

--- column-break ---

![Three-Tiered Model](attachments/Three-Tiered%20Model.png)

![Collapsed Core Model](attachments/Collapsed%20Core%20Model.png)

--- end-multi-column

# Spine and Leaf

--- start-multi-column: ID_78k6
```column-settings
Number of Columns: 2
Largest Column: standard
```

- Also known as <font color="#ffc000">CLOS network</font>, based on the founder Charles Clos.
	- This network is used exclusively in <font color="#ffc000">Data centers</font> with tons of servers.
- This network uses a very <font color="#ffc000">fast and redundant backbone</font> (spine) which connects to all switches (leaf) which then connect to host servers.
	- Switches do not connect directly to eachother. They only connect through the spine.

--- column-break ---

![Spine and Leaf Model](attachments/Spine%20and%20Leaf%20Model.png)

--- end-multi-column

# Traffic Flow
- <font color="#ff0000">North-South</font> (Vertical):
	- <font color="#ffc000">Southbound</font> traffic is data coming into your internal network from the internet.
	- <font color="#ffc000">Northbound</font> traffic is data going from the internal network to the outside internet.
- <font color="#ff0000">East-West</font> (Horizontal):
	- traffic going to and from devices within the network.
		- data replication, file transfers, inter-process communication.

















