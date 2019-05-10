# Case Study - JQAdams Windows Server

### Class: CMST 315

### 5/17/2019

### Names: Matthew Denholm, Nic Crombie, Caroline Reed, Wesley Elliott

**Objective:** Using the previous eight labs as a basis, Implement Active Directory objects and file structure for a company called J.Q. Adams Corporation.

**Equipment Used:**
1. 2 Windows 10 Pro Machines
2. Hyper-V Management Tools (Software)
3. Windows Server 2016 (Software)
4. Windows Remote Desktop Connection (Software)
5. Chrome Enterprise (guideline requirement)

**Questions:**
1.	What questions would you ask the company to help you plan the Active Directory?
  - What is the structure of the organization?
   - How are groups structured?

  - What are the resources they use?
   -  What applications/data are they using/tracking?
   -  File Sharing
   -  User Locations
   -  Printers?

  - What is their business model/process?
   - What data is the most important to them?
   - What data must be backed up?
   - What data must have High Uptimes?

  - What kind of policies do they require?
   - How secure do they want their employee accounts?
   - Where are they logging in from?
   - Local/Remote work?
   - VPN?

  - What is the technical level of the users?
   - User accessability/language?
   - User Experience and control surveilence/oversight

  - What are the naming conventions I.S. uses? (Topology)

  - How well is the company growing? Do you plan on expansions anytime soon?

2.	Describe your Active Directory structure including OUs, users and groups.  Include any assumptions you made about the company that affected your design.  (You could use something like Visio to display the structure.)

![pic]()

  - We assumed that the current location will not expand.
  - Other locations may be added in the future.
  - We're assuming that the general structure of the Active Directory won't change as they expand.

3.	Describe your file directory structure you created for the JQ Adams case study.  Indicate which folders are being shared.
  - One namespace folder containing all server files
  - Two main folders determining which server they are hosted on.
  - Admin folder contains programs, accounting system, reports folder, special access folder, HOME shared folder for users.
  - Production folder contains tracking system, Production HOME shared folder for users.
  - Program folders hidden because users don't need to mess with them, they should be installed on client computers by default.

4.	What is your naming policy for user accounts?
  - First Letter of First name then full last name. All Lowercase.

5.	Describe how you can delegate full control of managing production user accounts to the Production Vice President.
  - In Active Directory Users and Computers, On the Production OU, right click the OU Folder and select *Delegate Control*.
  - Add the user that will control the users in the OU
  - Select the permissions necessary to give that control.

6.	Describe how you use global groups to group users together and then domain local groups to provide access to network resources.  For example, you could describe how you used this concept to provide access for finance users to the AcctSys folder.
  - Global groups were used to assign access to necessary parts of the domain files.

7.	Generally speaking, what are the advantages of using global groups to manage users and then using domain local groups on the Security Tab to provide access?
  - In Larger companies, if there are specific groups of users that move around a lot, specifying which domain they are working in makes it a lot easier than changing policies on global groups. It also makes it easier to maintain Domain Local Groups from one location than logging in as a manager on a server to edit global groups.
  
8.	Why is it important to set disk quotas for users?
  - Users are only allocated the necessary space required to achieve the task.
  - Reduces costs if they are paying for cloud storage.
  - In game design, preventing a game from getting too large can be partially achieved by keeping files under a limit.

9.	Briefly describe how you setup DFS for your JQ Adams project.
  - Created a namespace called PublicT2 (The first attempt bugged out due to an overlength server name)
  - A folder called Administration was created on the admin server (and apporpriate sub folders). 
  - A folder called Production was created on the production server (and apporpriate sub folders).
  - In Distributed File Management, we added the two folders from each server.

10.	What are at least two advantages of using DFS?
  - If one server goes down, it is replicated onto the other server.
  - It can be accessed from any domain (assuming resources are allowed to be accessed)

11.	What group policies did you setup for this project?
  - Password Management
  - Idle Lockout Time
  - System & Software Defaults

12.	What information can you get from the GPresult tool?
  - GPresult shows you all the Domain applied policies and preferences for the computer and the user.
  
13.	Describe how you can use Group Policy to distribute and control Chrome on the client computers.
  - Group policies can be set up for different versions of chrome to be used with different clients. If some users require more security and site limitations, then different versions of chrome can be distributed to different users to achieve the work required.

14.	Explain how roaming profiles can be useful.
  - Roaming profiles allow users to have a consistent desktop experience regardless of the location or computer they log on to.

15.	Describe problems or issues you had while implementing this project.  How did you work around or overcome the problems?
  - We decided to develop Two brand new virtual servers for the project due to some issues with the previous labs. The name length of one of the servers created an issue with DFS, because windows server won't find server names over a length of 15 characters. This was fixed by renaming one of the servers to a name that fit the length requirement.
  - Our Hyper-v manager was having troubles connecting to our server. We had to borrow another group's Hyper-v manager that was connected to our server to manage it.
  - Remote access from the client IP address was denied because it wasn't enabled. While I want to say we forgot to enable PSRemoting, the fact that it worked on the previous servers doens't help to understanding why this didn't work. The work around was accessing via the Hyper-V manager.

**Conclusion/Reflection:** *Include what you learned and what you would do different if you were to start over on a similar project.*

This case study project provided an opportunity to better grasp the difficulty of setting up and/or maintaining a server for many users. In general, I learned how to set up a basic server, how to create a domain, create client users, apply basic policies to those users, and sync folders and files across the domain via Distributed File Service. There is a lot of variables to consider when setting up a server. If I were to start this over again, I would first make sure Naming conventions are more fluent (and within technological limitations). I would also spend more time on paper determining active directory structure, and more time on client requirements. I would also research a bit more as to what client requests are feasible and what requests aren't. Overall, this project provided a good beginners experience in the IT field of server management.