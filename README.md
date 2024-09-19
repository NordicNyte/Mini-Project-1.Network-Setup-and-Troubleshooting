# Configuration Guide

## Objective:
Simply put, a network is composed of interconnected items or devices that interact with each other. In this example, we're creating a network that includes all sorts of devices such as printers, phones, TVs, tablets, PCs, laptops, and servers. In the process, we’ll be enabling these devices to communicate with each other as well as with external networks. This will include assigning IP addresses, configuring subnet masks, as well as implementing hardware ranging from routers, switches, and DNS servers. The primary objective is to dive into the physical backbone of a network and understand how each device engages with the rest of the network.

## Use Cases:

- **Surfing the Web**: When you type a website's domain name into a browser, your computer doesn’t actually search for the name. Rather, it requests the IP address of the website from a DNS server to find the corresponding IP address. Which then is sent back to the browser, and converted to the corresponding webpage on the UI.

- **Gaming on a LAN**: When players cooperatively play on a LAN, each PC is wired into a switch via ethernet cables. This allows for peer-to-peer communication between the computers with low latency (delay in information travel) and enables both PCs to send and receive information such as player position, if items are used, a gun is shot, etc.

- **Transferring a File on a Server**: A device sends a request to a DNS server to retrieve the IP address of a domain name. Once the IP address is found, you can access the server hosting the file or webpage.

- **Accessing another PC/Host from your Laptop**: If you had your personal computer in another room and needed to access your work-based stand-up PC in your main office. You send a request from your own laptop to the work PC, the switch on the network directs your request based on MAC addresses, or ARP (Address Resolution Protocol) if the laptop doesn’t know where the PC is, to find what port the PC is located in. After, a session of continual data is shared between both, allowing you to access your work PC from your laptop.

---

## Steps to Set Up a Network

### Objective:
Build a network with devices such as laptops, PCs, printers, tablets, and servers. Include web and DNS servers, and enable connectivity within a LAN and to external networks.

### Step 1: Devices
- Add end devices (laptops, PCs, printers, tablets) and servers (web, DNS).  
  On Packet Tracer, this can be done by selecting the **End Devices** category on the top row of the bottom-right menu selection, then selecting whichever end device needed from the menu selection to the right of that.  
  Then drag them onto the network blank space.

- Use a switch for local network connectivity and a router to enable communication between different networks.

- **Repeat** this step again with a separate set of end devices.

### Step 2: Switch Setup
- Add a switch and connect devices using **Copper-Straight Through** cables.  
  On Packet Tracer, this can be done by selecting the **Networking Devices** category on the top row of the bottom-right menu selection, then selecting the **Switch** on the row below. After that, pick your needed switch from the menu selection to the right and drag it into the network blank space.

- Connect end devices, making sure to connect them to **FastEthernet** ports rather than **GigEthernet** ports on the switch.

![Alt text for Image 1](./Image%201.png)

- **Repeat** this step again with the other set of end devices.

![Alt text for Image 2](./Image%202.png)

### Step 3: Router Setup
- Add a router, power it on, and connect it to the switch.  
  In Packet Tracer, select the **Networking Devices** category from the bottom-left corner, then click on the **Routers** subcategory. Choose your desired router from the menu selection on the right and drag it into the network blank space.

- Connect the router to the switch using **Copper-Straight Through Cables**:  
  Click on the **Connections** tab at the bottom, select **Copper-Straight Through**, then click on the **GigabitEthernet 0/0** port on the router and connect it to an available **FastEthernet** port on the switch.

- **Power on the Router**:  
  Click the router, navigate to the **Physical** tab, and ensure that the power switch is toggled **ON**.

  ![Alt text for Image 3](./Image%203.png)

### Step 4: IP Configuration
- **Assign IP Addresses to the Router**:
  - Click on the router, go to the **Config** tab, and then click on the **GigabitEthernet 0/0** interface.
  - Under the **IP Address** section, assign the router a WAN IP address from the appropriate network, such as **172.16.0.1**.
  - Enter the **Subnet Mask** as **255.255.255.0** (for a /24 network).
  - Click **ON** for the interface to enable it.

![Alt text for Image 4](./Image%204.png)

- **Assign IP Addresses to End Devices**:
  - For each end device, click on it, navigate to the **Config** tab in Packet Tracer, and select the **FastEthernet 0** interface.
  - Set the IP address according to your network plan, e.g., **192.168.0.2** to **192.168.0.62** for devices in the **192.168.0.0/26** subnet.
  - Assign a **Subnet Mask**
 
![Alt text for Image 5](./Image%205.png)

### Step 5: Default Gateway Configuration
- **Set the Default Gateway for End Devices**:  
  For each end device, click on the device in Packet Tracer, go to the **Config** tab, and under the **FastEthernet** section, scroll down to find the **Default Gateway** field.  
  Set the Default Gateway to the IP address of the router's LAN interface (e.g., **192.168.0.1**).

![Alt text for Image 6](./Image%206.png)

### Step 6: DNS Server Setup
- **Add and Configure a DNS Server**:
  - In Packet Tracer, go to the **End Devices** tab, select a **Server**, and drag it into the workspace.
  - Click on the server, go to the **Config** tab, and select **DNS** from the left panel.
  - Enable the DNS service by toggling it on.
  - Add domain name mappings (e.g., map `example.com` to **192.168.0.10**, which is the IP of the web server).

### Step 7: Testing Connectivity

- **Ping Devices**:
  - Open the **Desktop** tab of any end device, then open the **Command Prompt**.
  - Click on the device, navigate to the **Desktop** tab, then click on the **Command Prompt** application on the UI.
  - Test connectivity by typing `ping [destination IP]` (e.g., `ping 192.168.0.1` to test communication with the router).

- **Test DNS Resolution**:  
  From the **Command Prompt** of any device, type `ping example.com` (assuming `example.com` is configured in the DNS server) to test DNS name resolution.

- **Use Packet Tracer Simulation**:  
  On the bottom-right of the UI, look for the **Simulation** button, use that to test all aspects of your network.

![Alt text for Image 7](./Image%207.png)

---

# FAQ

### 1. Why can't I ping between devices on different LANs?
- **Common Issue**: Devices on different LANs cannot communicate with each other via ping.
- **Possible Cause**: The router interfaces might not be configured correctly, or devices may not have the correct default gateway.
- **Troubleshooting Steps**:
    1. Verify the IP address configuration on each router interface to ensure it's correct for each LAN.
    2. Check that each device has the correct default gateway set to the router’s LAN IP (e.g., on LAN 1, the default gateway should be the router's IP like `192.168.0.1`).
    3. Make sure all devices are connected to the correct switch ports with copper straight-through cables, and that the ports are active.
- **Best Practice**: Double-check router interface configurations and ensure each LAN device has the correct gateway set.
- **Tips for Maintenance**: Regularly review the router configuration and document the IP addressing scheme for clarity.

---

### 2. Why can’t I access the web server using its domain name?
- **Common Issue**: Devices can't access the web server by domain name but can access it by IP.
- **Possible Cause**: The DNS server might not be properly configured, or the DNS server is not resolving domain names correctly.
- **Troubleshooting Steps**:
    1. Check that the DNS server has a static IP and is configured to resolve the web server’s domain name to its IP.
    2. Verify that the devices are configured to use the DNS server's IP address in their network settings.
    3. Ensure the DNS server is running, and test it using the `nslookup [domain name]` command.
- **Best Practice**: Ensure the DNS server has the correct IP mappings for each domain, and that all devices are pointed to the correct DNS server.
- **Tips for Maintenance**: Regularly test domain resolution, and ensure any IP changes are updated in the DNS server immediately.

---

### 3. Why are some devices not able to communicate with the DNS or Web server?
- **Common Issue**: Some devices cannot communicate with the DNS or Web server, even though others can.
- **Possible Cause**: There could be an incorrect static IP configuration on the devices or a wiring issue with the copper straight-through cables.
- **Troubleshooting Steps**:
    1. Confirm that each device has a unique static IP within the correct network range and the correct subnet mask.
    2. Verify that the DNS and Web servers are connected properly using copper straight-through cables and have functioning Ethernet ports.
    3. Use the `ping` command to test connectivity from the devices to both the DNS and Web server IP addresses.
- **Best Practice**: Ensure every device has a unique IP address and check that all devices are using the correct subnet mask.
- **Tips for Maintenance**: Periodically inspect cables and ensure IP addresses are properly documented and assigned.

---

### 4. Why do I experience intermittent connectivity to the Web server?
- **Common Issue**: Devices experience intermittent connectivity to the Web server.
- **Possible Cause**: Loose cable connections or a misconfigured network device may be causing network disruptions.
- **Troubleshooting Steps**:
    1. Check the physical connections to the Web server, ensuring all copper straight-through cables are securely plugged in.
    2. Ensure the Web server’s Ethernet port is working correctly and that there are no conflicting IP addresses on the network.
    3. Verify that the Web server has a static IP and that its configuration is correct.
- **Best Practice**: Regularly inspect cables and ensure that all devices have static, non-conflicting IP addresses.
- **Tips for Maintenance**: Periodically check physical connections and test connectivity to the Web server from multiple devices.

---

### 5. Why isn’t the DNS server resolving domain names for any devices?
- **Common Issue**: The DNS server is not resolving domain names for any devices on the network.
- **Possible Cause**: The DNS server might not be running, or its configuration might be incorrect.
- **Troubleshooting Steps**:
    1. Ensure the DNS server is powered on and running its DNS services.
    2. Verify that the DNS server has a valid static IP and that its IP matches the one configured on other devices as their DNS server.
    3. Check the DNS server’s configuration to ensure the correct domain name-to-IP mappings are in place.
- **Best Practice**: Always assign the DNS server a static IP and ensure that all devices use it for DNS queries.
- **Tips for Maintenance**: Periodically review and test the DNS server’s configuration to ensure it resolves domain names correctly and that all devices have the correct DNS IP set.

## Retrospective

### Challenges Faced and How They Were Addressed:
Throughout this project, I encountered several challenges that helped me refine my skills in networking and troubleshooting. One of the primary challenges was ensuring that all the **ports were properly connected** between devices like switches and routers. It was crucial to double-check each connection and use the correct wire types, such as copper straight-through cables for connecting end devices. Another challenge I faced was **assigning static IP addresses** accurately. In some cases, devices weren’t communicating due to minor errors in the IP addressing scheme. I resolved this by carefully reviewing each IP address and ensuring the correct subnet mask and default gateway were assigned to each device.

Additionally, configuring the **web and DNS servers** presented its own set of obstacles. Making sure the DNS server was correctly resolving domain names to the web server’s IP required careful attention to detail in configuring both devices and ensuring they were reachable on the network.

One of the most significant technical challenges was **learning how to subnet**. I had to understand how to break a network into smaller subnets and ensure that each subnet had enough IP addresses for the devices in that segment. Initially, this was confusing, but I practiced by manually calculating subnets and verifying the results by implementing them in the network.

### New Skills and Insights Gained:
This project was a comprehensive learning experience that allowed me to gain several new skills and deepen my understanding of networking fundamentals. One of the key skills I developed was **building a network from scratch**. This involved understanding and working with critical network components such as **routers, switches, end hosts, wire types, DNS servers, NAT, ARP, and subnetting**.

I learned how to configure each of these components both in theory and practice, utilizing a **Command Line Interface (CLI)** for many configurations. This hands-on approach to networking helped solidify my understanding of how data moves through a network and how each device plays a role in ensuring seamless communication. Moreover, learning how to **subnet** and manage IP addresses efficiently was a valuable takeaway that I will continue to apply in future networking projects.

Another major insight I gained was the importance of **network troubleshooting**. From using commands like `ping` to verify connectivity, to checking configurations for potential missteps, I learned how essential it is to break down a problem into smaller steps and address each one systematically.

### Areas for Improvement:
While I made significant progress during this project, there are still several areas where I could improve in future network configurations. The first area is **subnetting**. Although I learned how to subnet, I feel that additional practice is necessary to become more confident in quickly and accurately calculating subnets, especially in more complex scenarios involving multiple subnets.

Another area for growth is adding **wireless connections** to a network. In this project, I primarily focused on wired networks, but wireless networking is equally important, especially in today’s environments. Learning how to configure wireless access points (WAPs) and integrating wireless devices into the same network would enhance my skill set and make me more versatile in network design.

---

By reflecting on these challenges, new skills, and areas for improvement, I can continue to grow as a network engineer. My ability to troubleshoot and solve technical issues has significantly improved through this project, and I look forward to building on this foundation in future endeavors.

