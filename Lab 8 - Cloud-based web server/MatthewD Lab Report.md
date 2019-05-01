# Lab 8 - Cloud-Based Web Server

### Class: CMST 315

### 5/3/2019

### Names: Matthew Denholm, Wesley Elliott

**Objective:** Create a Virtual Online Server with Microsoft Windows Server or Linux Server in Microsoft Azure.

**Equipment Used:**
1. PuTTY (Remote Desktop Software)
2. Firefox (Web Browser)
3. Microsoft Azure

**Notes and Observations:**
The first step in this process was getting an account on Microsoft Azure. You need a Microsoft account for this, which is a similar process to that of most other accounts. Once the account was created, $200 credit was given as a trial.

Azure gives the option of using Windows Server 2016 or Linux. I opted for Linux, and the tutorials can be accessed via the link in the references section of this lab report. The tutorial wanted to work through the command line version of setting up the server, but after hardly being able to get the azure command line to work for me (Its not the same as command prompt, or linux terminals), I opted to go the route of seeing if the GUI version would be easier, and quicker.

The experience was very similar to setting up/installing tools on a windows 2016 server. Sections such as basics, disks, networking, and management were all included. The form was straight-forward, free trial subscription, easy to name a virtual machine, a variety of disk images to choose from, and the classic username and password setup. You had the option of how advanced the hard-drive was (HDD or SSD), and how big it would be. Networking configurations could be auto-generated or set by default. There wasn't any chance that a command could be typed wrong, or a variable in a command was missing. Plus the form showed what was required, and what wasn't.

After all of the settings were inputted and set, the virtual machine, along with several other necessary resources for functionality (storage accounts, network interfaces, and recovery services), was created. Many of the other steps in the tutorial (In this case steps 2-14) were already accomplished in the process of creating the virtual machine via the form. The goal of this lab was to set up a web server, and linux had 3 options. I went with Apache in this lab, and so step 15a was the one I followed.

At this point, we needed access to the machine itself. Because I didn't specify any ports to allow in the creation of the virtual machine, I had to open one. This was accessed by going to the *Dashboard -> VM -> Networking Settings -> Add inbound port rule*. For this lab, Port 22 was opened for installation and development, and later port 80 was opened for testing in the web browser.

![pic](https://github.com/Matthew-Denholm/Sys-Administration-Lab-Reports/blob/master/Lab%208%20-%20Cloud-based%20web%20server/Port%20Rules.PNG)

There wasn't much getting around the command line at this point. It could've been accessed via the azure command line (bash), but I had a different tool available called PuTTY. PuTTY is a remote desktop software without the fancy live GUI (Like windows remote desktop connection). Once signed in, I copied the following command from the tutorial:

**sudo apt update && sudo apt install lamp-server^**

After the installation was completed, serveral verifications were done.

**apache2 -v**
**mysql -V**
**php -v**

After verifications were complete, I logged out, and tested it in a web browser. The default page appeared, and the lab was successful.

**Questions:**
1. What are some advantages and disadvantages of using cloud­based architecture?
  - Advantages:
    - Scalable.
	- On Demand.
	- Less hardware investment
  - Disadvantages:
    - Less control on the hardware side.
	- Trust in host provider (if they go down, you could go down as well)
2. What type of things does a business need to consider before moving IT functions to the cloud?
  - Is it in our company's best interest (goals and mission) to move functions to the cloud?
  - Will this save costs by moving to the cloud?
  - Will there be better security benefits by moving to the cloud?
3. Give some examples of some built­in configurations and services provided by Azure.
  - Public IP address
  - Backups
  - Network Interface
  - Vault Recovery

**References:**
- https://docs.microsoft.com/en-us/azure/virtual-machines/linux/

**Conclusion:**
This lab provided a basic exposure to cloud computing and basic functionality of online virtual machines. It also showed how easy it can be to set up a virtual server online. There are lots of options that can provide practically limitless customization to cloud servers, but you do have the downside that if the host provider goes down, you also go down. The major problems I could see were commands not accurate due to software updates since the time of the writing. The GUI was much easier to follow and therefore set up.
