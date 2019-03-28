# Lab 5 - Distributed File System

### Class: CMST 315

### 3/28/19

### Names: Matthew Denholm, Nic Crombie, Caroline Reed, Wesley Elliott

**Objective:** The objective of this lab is to add a second domain controller and configure that server with DFS with replication.

**Equipment Used:**
1. 2 Windows 10 Pro Machines
2. Windows Server 2016 (Software)
3. Windows Remote Desktop Connection (Software)

**Notes and Observations:** The first step in this lab was setting up active directory on our other virtual server. First, the server was renamed (WinServer1a in our case), and its IP address was set to static. Primary DNS was changed to the WinServer1b address. This joins the two servers under the same domain.

Our servers then needed active directory. This was done by using the server manager, and adding roles and features, like before in lab 4. Active Directory options were then selected an installed. Because we already had a global catalog set up for server 1b, and an existing domain name, we unchecked those features. Once set up, a client sign-in test was performed and was successful.

The servers are now under the same domain, but cannot yet share with each other. On our server 1b manager, under roles and features, the Distributed File service role was enabled. More options were set up to allow it to start functioning. A new namespace was made called public data, and the host was set to 1b.

On 1a, a new folder with a couple text files was created. It was then shared via the methods in lab 4. DFS was then enabled, but the only thing that was needed was folder validation.

A final client test showed that both folders from different servers were able to be seen.

**Questions:**
1. What advantages does DFS offer over regular folder shares?
  - Distributed file systems allow users to access data that is on all the servers from any connected network. It also serves as a central hub for easier management of files rather than having to request files from separate networks.
2. What advantages does domain-based namespace have over standalone DFS?
  - Information is stored in the active directory, and unlike a standalone DFS, there is some fault tollerance, as well as multiple pointers to the same resources. If something goes down, then there are backups.
3. What is the purpose of the referral server in DFS? Why is it important to have a backup referral server?
  - The main purpose of the referral server is to determine where DFS Information is saved. The referral is an ordered list of targets, and when the client receives this list, they try to access the first one in the list.

**References:**
1. https://nedimmehic.org/2017/10/05/how-to-install-and-configure-distributed-file-system-dfs-2016-part-1/
2. https://nedimmehic.org/2017/11/01/how-to-install-and-configure-distributed-file-system-dfs-2016-part-2/

**Conclusion:** This lab successfully set up a DFS across two VM servers. The major issue that happened during this lab occurred at the end, where the DFS was automatically set up, preventing any manual changes. Other than that, this lab was extended learning from lab 4, further working with groups and permissions, except this time learning how to control permissions across multiple servers.