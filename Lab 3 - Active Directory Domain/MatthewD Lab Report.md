# Lab 3 - Active Directory Domain

### Class: CMST 315

### 3/7/2019

### Names: Matthew Denholm, Nic Crombie, Caroline Reed, Wesley Elliott

**Objective:** Our objective is to promote the server to a Local Domain and add a client computer to understand how Organizational Units, Groups, and Users operate in a Domain Environment.

**Equipment Used:** 
1. 2 Windows 10 Pro Machines
2. Windows Server 2016 (Software)
3. Windows Remote Desktop Connection (Software)
4. Windows 10 Installation File (Software)

**Notes and Observations:**
This lab begun in the same state where lab 2 ended. The first step of this lab was to prepare the system for cloning. This initial server will be used as a clean state to make copies from. Should something go down, there is a backup state from which clients can start from.

Preparations were made through the sysprep command. After shutting down the VM, The server image was exported via the Hyper-V Manager Tools. For this lab, they were stored to (This location). A new virtual server was then imported via the copied VM image.

Once bootup procedures completed, The IP address and relative information were set to static. Like previous instances, this removes the possibility of other systems losing contact with the server. The server was also given a new computer name, which was provided by the instructor (This makes things easier later on in the lab).

After a restart, Active Directory was set up. (see images for set-up process).



**Questions:**
1. Why Change the Preferred DNS Server on the Client?
- This step was taken to ensure that all new clients that are added to they server are connected through the server. This helps to ensure privacy, and maintain a stable connections speed.
2. Why extra step was required to allow the client to log in with a domain user? Why was this requirement added by Microsoft?
- The extra step was going through the control panel and adding the users separately. It adds an extra layer of security.
3. Advantages of Active Directory over regular servers:
- You can connect to multiple servers.
- Doesn't store passwords (more secure).
4. List some reasons why companies use Virtual Servers.
- Saves electricity (less hardware producing heat, saving climate conditioning costs).
- Saves buying additional hardware
- Easier to secure (physically).
- Easier to clone (and update), which creates better uptime consistency should a server go down.

**References:**
1. https://blog.netwrix.com/2017/04/20/tutorial-learn-the-basics-of-active-directory/
2. https://www.netwrix.com/active_directory_group_management.html

**Conclusion:** This lab allowed a successful cloning of a virtual server, as well as a successful installation of a virtual client machine. The only major hiccup while doing this lab was setting up the virtual client, as a corrupted image of Windows 10 was causing issues. A new image was downloaded and used, and the rest was smooth sailing afterward. It also taught introductory administrative tasks.