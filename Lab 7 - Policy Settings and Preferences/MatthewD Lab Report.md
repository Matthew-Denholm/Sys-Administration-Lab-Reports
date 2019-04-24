# Lab 7 - Policy Settings and Preferences

### Class: CMST 315

### 4/23/2019

### Names: Matthew Denholm, Nic Crombie, Caroline Reed, Wesley Elliott

**Objective:** Familiarize with actual policy settings within Group Policy Objects.

**Equipment Used:** 
1. 2 Windows 10 Pro Machines

2. Windows Server 2016 (Software)

3. Windows Remote Desktop Connection (Software)

**Notes and Observations:**
This lab started off by wanting to make a change to comptuer settings. A new policy called Idle Timeout was created and applied to the domain. The setting *Interactive Logon* was under **Computer Configuration -> Policies -> Administrative Templates -> System -> Login**. It was changed from *Not Configured* to *30 Seconds*. Initially, the clients were not experiencing these changes, even after a gpupdate command. The professor recommended trying to move the clients into a new OU. In our Active Directory settings, a new OU called **My Computers** was put in the domain. A virtual Client was then moved to that folder.

Further tests showed that the policy was not showing because the command promt wasn't running in administrator mode. Becasue of this, **gpresult /r** commands were only showing User policies, and not the Computer policies. Launching in Administrator mode gave expected results.

The next Experiment involved default startup programs. In our Test, we used File explorer and the calculator. The quickest way to get the file path was to open the program, then open task manager. Right click the program, then selected *open file location*, then copied the path into the policy setting's path field. File Explorer happened to be in the same location as the server admin's, but the calculator on the client wasn't the same version as the one on the server, and therefore the calculator didn't boot upon logging in. Finding the proper path on the client, the policy setting was updated and successfully booted upon logging in a second time.

Returning for the next class period, the *Idle Timeout* policy happened to be affecting the server itself. This isn't ideal in our testing situations, so it was attempted to be removed. Every User was stuck with a 30 second lockout. After many variations of trying to remove it, (First by changing the timer form 30 seconds to 600 seconds, then disablement, to finally complete removal), it was eventaully just left as is. This wasn't an event breaking issue, but an annoyance that may have to be embraced for the remaining labs.

The last section of this lab focused on preferences. There were two in particular, Drives and Printers. Drive mapping relates to our Distributed file service. We can set a folder that is shared with clients as a network drive. This was accomplished by creating a new GPO, and going to that new GPO's Editor. Drive map was created by going to **User Configuration -> Preferences -> Windows Settings -> Drive Maps**, Right clicked and selected **New -> Mapped Drive**, inputted the location of the drive (in our example, *\\Domain1.local\PublicData*, labeled *Public Data*) and assigned a letter (M). The GPO was then linked to a client OU. A client update showed the drive map under the "Network locations" in File explorer for easier access.

Finally, a new GPO was created for printer connections. In the GPO's editor, a new printer connection preference was established by going to **User Configuration -> Preferences -> Control Panel Settings -> Printers**. Similar to drive mapping, we right-clicked and selected **New -> Shared Printer**, added the path of the printer (in our example, *\\WinServer1b\GTO*) and set it as a default printer. Like the drive map, it was linked to a client OU. A client update didn't immediately show the printer, but searching and adding it via the control panel caused it to appear.


**Questions:**
1. How is a preference different from a policy setting?
  - Preferences modify registry configurations, while policies do not (They store in their own isolated registry.
  - Policies disable some settings, and are managed by an administrator. Preferences are default settings an administrator sets, but can be modified by a user.
2. How does the Administrative Template sections of GPOs provide flexibility to Group Policy?
  - Administrative templates are divided into multiple categories, meaning administrators have lots of flexibility as to what settings can affect what categories. Administrative templates can also be custom made, which also allows admins to affect settings that may not normally be available by default.
3. Give example of some of the settings an admin can control in the Computer Configuration section.
  - Network Configurations
  - Boot Settings/Shutdown Settings
  - Application Installations
  - Hardware Installations (Like Printers)
4. Give example of some of the settings an admin can control in the User Configuration section.
  - Idle Timeouts
  - Network Drives
  - Application Access (only certain visible applications)
  
**References:**
- https://www.safaribooksonline.com/library/view/mastering-windows-group/9781789347395/?orpq

**Conclusion:**
This lab provided a basic understanding of preferences, as well as further exposure to policy settings. Again, there are lots of options, and proper documentation of policies and preferences is crucial to avoid complications. The major hiccup in this lab was strangely not being able to fully resolve the Idle Timeout policy, as even after removal it continues to lock out after 30 seconds. Overall, it was a good learning experience.
