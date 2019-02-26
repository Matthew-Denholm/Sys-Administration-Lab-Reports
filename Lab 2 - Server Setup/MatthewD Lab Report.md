# Lab 2 - Server Setup

### Class: CMST 315

### 2/21/2019

### Names: Matthew Denholm, Nic Crombie, Caroline Reed, Wesley Elliott

**Objective:** The objective of this lab is to install a server OS on a rack server and create/run a virtual machine using Windows Server.

**Equipment Used:**
1. 2 Windows 10 Pro Machines
2. Hyper-V Management Tools (Software)
3. Windows Server 2016 (Software)
4. Hyper-V Server 2016 Installation DVD
5. Windows Remote Desktop Connection (Software)
6. A Dell rack Server

**Notes and Observations:** To begin this lab, we had to make sure our server was set up properly. The server had 2 drives, each about 72 GB in size. It was possible that these servers were set up to be in RAID1, a state that mirrored the drives instead of allocating both for available space. That state is RAID0, which is what we needed to confirm the drives were using.

It was also possible that the servers had some previous partitions or other software running on them already, so when installing Hyper-V Server, We had to delete all current partitions and create a single partition for the Hyper-V Server software. Software was then allowed to be installed. Account information was provided by the instructor.

After Installations were complete, the network connections were set to static IPs. These addresses were also provided by the instructor. This was done to ensure that a remote connection to the server was obtainable and always known. Having a server that obtains a random IP address should it be rebooted creates a guessing game should anyone need to connect to it. The Server Names were also Updated for Lab Formats (essentailly names provided by the instructor). Remote Desktop Capabilities were also enabled.

After all Preparations were complete, remote connections were attempted from the Lab computers. This proved unsuccessful due to firewall complications and limitations. Later we setup/used separate Windows 10 Machines That did not have as many firewall limitations and managed to get server connections from there. Using Hyper-V management tools, a connection was set up on the Windows 10 machines.


In attempts to connect from the lab computers, some settings were adjusted to try and remote connect. Using a Windows Powershell (Command Prompt), two commands were run.
![pic](https://github.com/Matthew-Denholm/Sys-Administration-Lab-Reports/blob/master/Lab%202%20-%20Server%20Setup/Capture.PNG)
This would remove any barriers blocking connection from the computer to the server. This attempt didn't prove to be enough to break through the firewall, however. Another attempt via editing Local Group Policies didn't pan out either. This led to the use of a separate machine not under the same restrictions as the lab computers, which proved successful.
![pic](https://github.com/Matthew-Denholm/Sys-Administration-Lab-Reports/blob/master/Lab%202%20-%20Server%20Setup/Capture4.PNG)
![pic](https://github.com/Matthew-Denholm/Sys-Administration-Lab-Reports/blob/master/Lab%202%20-%20Server%20Setup/Capture5.PNG)
![pic](https://github.com/Matthew-Denholm/Sys-Administration-Lab-Reports/blob/master/Lab%202%20-%20Server%20Setup/Capture5.5.PNG)

Once all settings were established and connections made, the first virtual machine was created. Once ran, it was installed with Windows Server 2016, and set up with appropriate account information (Provided by the instructor). To remote desktop into this virtual machine, the IP address was needed. This was found via network settings. The settings were changed to static, as they didn't match up with the correct IP address assigned by the server, so no actual internet connection was available, and therefore remote desktoping wasn't available. After this change, the server was online and operable.

**Questions:**
1. IP address, subnet mask, gateway address, DNS, and Alt DNS of Server: 
   - 10.136.212.42/22
   - 255.255.252.0
   - 10.136.212.1
   - 10.133.253.130
   - 10.133.253.131
2. Ethernet address to network interface
   - 10.136.212.42
3. Network ID of lab Network:
   - HYPER1 (server)
   - labs.salinak-state.edu
4. Host ID of computer:
   - Win10Pro1
5. Range of host IP addresses on subnet:
   - 10.136.212.1 - 10.136.215.254
6. Purpose of a default gateway:
   - To provide your computer with a connection to the internet. This is usually located with the ISP.
   - Can also be used to allow one host to talk with another host on a different subnet.
7. Symptoms of invalid Default Gateway:
   - Connection to the internet is not available.
   - Ability to remote desktop keeps failing.
   - Cannot log in on some subnets.
   
**References:**
1. https://timothygruber.com/hyper-v-2/remotely-managing-hyper-v-server-in-a-workgroup-or-non-domain/
2. https://www.petri.com/using-syspre-windows-10
3. https://www.nakivo.com/blog/creating-configuring-vms-in-windows-server-2016-hyper-v/
4. https://solveazure.com/2018/05/11/unable-to-rdp-to-virtual-machine-credssp-encryption-oracle-remediation/

**Conclusion:** The server was successfully installed with Hyper-V server and is successfully running a Virtual Machine running Windows Server 2016. One of the most significant errors was selecting the wrong port for the ethernet connection, as this didn't allow for an internet connection, just a lab connection. This was changed, and required re-inputting the network configurations on the server to take effect. This lab taught how to install and set up a server, and also taught an introduction to virtual machines.
