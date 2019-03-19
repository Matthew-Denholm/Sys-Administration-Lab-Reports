# Lab 4 - Groups and Permissions

### Class: CMST 315

### 3/7/2019

### Names: Matthew Denholm, Nic Crombie, Caroline Reed, Wesley Elliott

**Objective:** The objective of this lab is to manage permissions to resources by using Active Directory Groups.

**Equipment Used:** 
1. 2 Windows 10 Pro Machines
2. Windows Server 2016 (Software)
3. Windows Remote Desktop Connection (Software)

**Notes and Observations:** This lab began where it left off from lab 3. 4 new OUs were added to the directories. In one of those directories, we added 4 new users using the same method in lab 3. Passwords were provided by the instructor.

Once all the users were set up, they were added to a group. For this lab, all the client users were added to a global group called TestGroup. That group was then added to a domain group called DLGroup. The same users were then added/divided amongst two additional global groups (for practice, and was required by the lab). Two New Domain Local Groups were created, and one global group was added to each Domain Group. 

On the server, a new folder was created on the desktop. 4 additional folders were created inside of that. The desktop folder was shared on the domain, and was successfully able to be accessed by the clients, as were the subfolders as well.

On the security tab of the folder properties, the DLGroup was added, and given the permissions of Read and view. Certain subfolders were then selectively granted greater permissions for each user in the group. One was left default, one was given write (but not modify) permissions, one was given modify permissions, and a final one was blocked from being viewed.

Finally, a network printer was added, and a file in one of the test folders was successfully printed from one of the clients.

**Questions:** N/A

**References:** https://www.tactig.com/install-configure-print-services-windows-server/

**Conclusion:** This lab successfully set up multiple users on a domain, and also allowed for different users to have access to different resources. It also taught a bit more depth about permissions behind the scenes of windows users. Probably the most challenging aspect of this lab was knowing which groups/users to use when setting up the permissions.