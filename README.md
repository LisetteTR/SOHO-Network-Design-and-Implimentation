# SOHO-Network-Design-and-Implimentation
<p align="center">
<img height="80%" width="80%" alt="<img width="732" alt= "<img width="732" alt="Screenshot 2024-06-14 at 10 45 47 PM" src="https://github.com/LisetteTR/SOHO-Network-Design-and-Implimentation/assets/157552891/f178d668-2333-451f-aa93-ca999425a0bf">


</p>

<h1>Description</h1>

<p>This project involves the design and implementation of an enterprise network and a SOHO (Small Office/Home Office) network system using Cisco Packet Tracer. It includes creating and simulating enterprise and SOHO network designs, incorporating technologies such as VLANs, Inter-VLAN routing, DHCP servers, WLAN or wireless networks, configuring access points, and host configurations. Using the scenario below to have an idea of the type of network that is needed. </p>
<p>XYZ Company is a fast-growing company in Texas with more than 2 million customers globally. The company deals with selling and buying of food items, which are basically operated from the headquarters. The company is intending to open a branch in Austin, TX. Thus, the company requires a network engineer to design the network for the branch. The network is intended to operate seperately from the HQ Network.

Being a small network, the company has the following requirements during implementation;

A) One router and one switch to be used (all CISCO products).

B) 3 departments (Admin/IT, Finance/HR and Customer service/Reception)

C) Each department is required to be in diffrent VLANS.

D) Each department is required to have wireless network for the users.

E) Host devices in the network are required to obtain in IPV4 addresses automatically.

F) Devices in all the departments are required to communicate with each other

Assume the ISP gave out a base network of 192.168.1.0, as the network engineer who has been hired, design and implement a network considering the above requirements.</p>
<br />


<h2>Environments and Technologies Used</h2>

- VLAN & Inter VLAN Routing
- Configure DHCP Server
- Configure WLAN & WAPs
- VLAN Trunking
- subnetting

<h2>Operating Systems Used </h2>
- cisco packet tracer on MacOS<p>

<h2> Steps for configurations </h2>


  
<img width="80%" height="80% Screenshot 2024-06-14 at 4 33 19 PM" src="https://github.com/LisetteTR/SOHO-Network-Design-and-Implimentation/assets/157552891/5c41f538-4dc2-4eb6-ace6-1cb5fe6bb0e7">


<p>
Step 1, "A) One router and one switch to be used" go ahead and drag a router and a switch to the center of the screen.
</p>
<br />
<p></p>
<img width="80%" height="80%" src="https://github.com/LisetteTR/SOHO-Network-Design-and-Implimentation/assets/157552891/d1f42f04-88c9-448c-9363-383f0a2057ff">


<p>
Step 2, "B) 3 Departments (Admin/IT, Finance/HR, and Customer service/Reception)" and is required to have WAP (Wireless Access Points) for the users, and connect connect all devices to the switch.
</p>
<br />

<p>
<img width="80%" height="80%" src="https://github.com/LisetteTR/SOHO-Network-Design-and-Implimentation/assets/157552891/612990eb-fe29-4db8-9939-384e7204509d">
</p>
<p>
Step 3, To keep netwrok organized, identify each departmment and VLAN to which they are going to be assigned to later along.
</p>
<br />

<p>
<img width="80%" height="80%" src="https://github.com/LisetteTR/SOHO-Network-Design-and-Implimentation/assets/157552891/c26c47c3-4d62-48be-b891-d9a0ac200167">
<img width="80%" height="80%" src="https://github.com/LisetteTR/SOHO-Network-Design-and-Implimentation/assets/157552891/37b7da8b-4add-4194-b36e-733228751f64">


</p>
<p>
Step 4, "C) Each department is required to be in diffrent VLANS." Start to identify all required VLAN IPs, Broadcast IPs, and IP ranges. Once VLANs are identified, go ahead and label your department's VLANs to keep organization.
</p>
<br />

<p>
<img width="100%" height="100%" src="https://github.com/LisetteTR/SOHO-Network-Design-and-Implimentation/assets/157552891/e3a65aef-9c25-45f5-a286-9d2192f4b36f">
</p>
<p>
Step 5, Start to configure VLANs in the switch.
  click on the switch > CLI > Press enter on the keyboard
  <p>
  Switch> enable > Switch# > configure terminal > Switch(config)# > Interface range fa0/2-4 > swithcport mode access VLAN 10 (REPEAT THESE STEPS FOR VLANs 20 & 30) > do write 
  > exit > do show start (once you hit enter, make sure VLANs are configure correctly to each interface.
</p>
<br />

<p>
<img width="80%" height="80%" src="https://github.com/LisetteTR/SOHO-Network-Design-and-Implimentation/assets/157552891/8884b0c4-7786-4551-a1fe-369fef0cd6ff">

</p>
<p>
Step 6, Configure the WAPs, set SSID to each WAP for each department ex: "Admin - WIFI", set authentication to WPA2-PSK  and set a password the will be remembered an repeat steps for each WAP. 
</p>
<br />

<p>
<img width="100%" height="100%" src="https://github.com/LisetteTR/SOHO-Network-Design-and-Implimentation/assets/157552891/45760bff-a914-4980-ab4d-368b28d17b81">

</p>
<p>
Step 7, All devices should be able to communicate with each other, therefore VLAN Trunking needs to be configured.
  <p>
  switch> enable > Switch# > Configure Terminal > Switch(config)# > Interface fa0/1 > switchport mode trunk > do write
</p>
<br />

<p>
<img width="100%" height="100%" src="https://github.com/LisetteTR/SOHO-Network-Design-and-Implimentation/assets/157552891/a1072871-ff36-4ab8-8d55-821d11e3dbc0">
</p>
<p>
Step 8, Configure the router to UP state: 
  <p> NO > Router> Enable > Router# > configure terminal > Router(config)# > Interface Gig0/0 > no shutdown > do write
</p>
<br />

<p>
<img width="100%" height="100%" src="https://github.com/LisetteTR/SOHO-Network-Design-and-Implimentation/assets/157552891/e8e86e18-8d8b-49ca-acf6-c119171f187a">
</p>
<p>
Step 9, Configure inter Vlan routing in router so all devices can communicate
</P>
Router(config)# > Interface gig0/0.10 > encapsulation dot1Q 10 > IP address 192.168.1.1 255.255.255.192 (got IP from 1st subnet's IP range) > exit > int gig0/0.20 > encapsulation dot1Q 20 > ip address 192.198.1.65 255.255.255.192 > do write > exit > interface gig0/0 .30 > encapsulation dot1q 30 > ip address 192.168.1.129 255.255.255.192 > do write > exit > do show start (to confirm all sub interfaces are configured.)

</p>
<br />

<p>
<img width="100%" height="100%" src="https://github.com/LisetteTR/SOHO-Network-Design-and-Implimentation/assets/157552891/310556eb-4b1f-44d1-9453-c1a498fc8a0f">
</p>
<p>
Step 10, Configure DHCP server.
  <p>
    router(config)# > service dhcp > ip dhcp pool Admin-pool > netwrok 192.168.1.0 255.255.255.192 > default-router 192.168.1.1 > dns-server 192.168.1.1 > domain name admin.com > exit (and repeat the same steps for all 3 interfaces VLAN) > exit > do write
</p>
<br />

<p>
<img width="80%" height="80%" src="https://github.com/LisetteTR/SOHO-Network-Design-and-Implimentation/assets/157552891/cea40a37-f37e-491c-a855-09b95105d75e">
</p>
<p>
Step 11, make sure devices are being assigned IPV4 addresses automatically 
</p>
<br />

<p>
<img width="80%" height="80%" src="https://github.com/LisetteTR/SOHO-Network-Design-and-Implimentation/assets/157552891/78f6bcbe-7e6b-4f24-898f-8f36cbe38722">
</p>
<p>
Step 12, Make sure all WAPs are working and devices are connecting to them.(smart phones and laptops) 
</p>
<br />

<p>
<img width="140%" height="140%" src="https://github.com/LisetteTR/SOHO-Network-Design-and-Implimentation/assets/157552891/f6e64d1a-c572-4bca-a4ce-1aad19174e3d">

</p>
<p>
Step 13, Test connectivity with all or some devices in diffrent VLANS and make sure it passes.
</p>
<br />

<p>
<img width="80%" height="80%" src="https://github.com/LisetteTrejo/Azure-Compute-and-Networking/assets/136425839/6b45ce5f-be2b-431b-b87f-0f2872c1ead8">
</p>
<p>
Step 14, Set your filter to DHCP traffic in wire shark. In the command line renew VM1's IP address using the ipconfig/renew command, and watch as traffic is being received.
</p>
<br />

<p>
<img width="80%" height="80%" src="https://github.com/LisetteTrejo/Azure-Compute-and-Networking/assets/136425839/04ba4b60-2d57-48d0-bb23-81767867557c">

</p>
<p>
Step 15, Set your Filter to DNS traffic and watch as some traffic comes through, In the command line see what Google's IP address is with the nslookup www.google.com command. As you press Enter, more traffic will be generated.
</p>
<br />

<p>
<img width="80%" height="80%" src="https://github.com/LisetteTrejo/Azure-Compute-and-Networking/assets/136425839/e54b609e-a974-40b7-8539-4ae5e61a830a">
</p>
<p>
Step 16, Set your filter to RDP and watch as traffic comes through. It should be non-stop traffic due to VM1 being a remote desktop.
</p>
<br />
