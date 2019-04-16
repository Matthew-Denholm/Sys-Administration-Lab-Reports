# Lab 6 - Group Policy Management

### Class: CMST 315

### 4/16/2019

### Names: Matthew Denholm, Nic Crombie, Caroline Reed, Wesley Elliott

**Objective:** The objective of this lab is to apply and familiarize Group Policy objects and processing with clients via the Group Policy Management Console.

**Equipment Used:** 
1. 2 Windows 10 Pro Machines

2. Windows Server 2016 (Software)

3. Windows Remote Desktop Connection (Software)

**Notes and Observations:**
The first thing done in this lab was creating a new GPO. In this case, we changed the wallpaper for a client. In the group policy management window, right click group policy objects, and new. Our name of this object was "Wallpaper <name>."

Because we didn't have any wallpapers to choose from, we had to import a few. These were put in a new directory folder on our DFS. The file locations of each of our wallpapers were then added to the directory in the Group Policy Object. These objects were then added to the Active directory group where all of our clients were.

We then tried logging in with each of our users. Some cases worked, some got the same background. Our Initial thoughts were that something went wrong on DFS, so we first combined all the wallpapers into one distributed folder. The same effect still remained, so we then tried separating each of the users into their own OUs. This lead to the intended result.

By next class period, our group had not realized that the password was on a change cycle. We were unable to log on without a password change, via client or server administrator. This was fixed by the instructor. After logging on with a new password, the policy settings were set to remove password reset times.

The next task was to intentionally cause a conflict with GPOs. Under one OU, Two wallpaper GPOs were applied. It was found that the policy on top is the one that is applied.

It was also possible to block GPO Inheritance. (see question 8, as it relates to this section of the report) Applying a wallpaper for the whole domain overrides all the policies that affect a wallpaper in the OUs, hence inheritence. Blocking it prevents this. See picture for how it was done. ![pic](https://github.com/Matthew-Denholm/Sys-Administration-Lab-Reports/blob/master/Lab%206%20-%20Group%20Policy%20Management/Capture.PNG) 

The next task was to Enforce a policy. Wherever the policy is placed, enforcing it ensures that it will place its order of application first. If it is above a blocked inheritence OU, it should still be applied, or at the very least show up in the client group policies. ![pic](https://github.com/Matthew-Denholm/Sys-Administration-Lab-Reports/blob/master/Lab%206%20-%20Group%20Policy%20Management/Capture1.PNG)

The Final major task done in this lab was GPO Filtering. A wallpaper policy was applied on the domain level. A filter was then set up to apply that filter to a specific group of users on the network (Ours was TestGroup). One client was then filtered out of that wallpaper policy. The result was that user not having a custom background. Timed policies were also tested. In this lab, we just tested changing the day they are applied.


**Questions:**
1. Why is it so important that IT administrators learn Group Policy in an Active Directory 
environment?
  - Group Policy and Active Directory is important to learn because it allows everyone to work in a more secure and controlled environment. It allows you to protect data more easily, and allow specific data to be accessed by certain individuals.
2. What are the levels of hierarchy for Group Policy and how do they fit together?
  - Group policies are applied from top to bottom. Those applied to OUs will be inherited in all domains, sites, and local computers. Those applied to a domain are applied to all sites and computers, etc etc...
3. By default, what is affected by the Default Domain Policy GPO?
  - Password history
  - Password Length
  - Ticket lifetime
  - logon restrictions
4. Often you will find policy settings with three choices: Not Configured, Enabled, or Disabled. Explain why Not Configured and Disabled might not be the same.  Give an example.
  - Not Configured means that external variables can put the policy in a state of enabled or disabled. Or it may have no effect at all by default.
  - Disabled means that no matter what variables are changed, they will not activate the policy. The policy cannot affect anything until enabled to do so.
  - Notifications are good examples. Most by default aren't configured immediately. That means they may send a notification when a task finishes, or sometimes not. Until they are enabled, or disabled, they may only do specific ones, all of them, or none of them.
5. Explain why creating new GPOs rather than modifying the Default Domain Policy is generally a better idea.
  - Leaving the Default Domain Policy gives you a fallback policy in case something messes up.
  - Creating New GPOs allows you to better sort which settings are being modified.
  - You can create multiple GPOs that change the same settings, but are different for other users. This wouldn't always be possible changing one GPO.
6. Along the same line as the previous question, why is it best to keep minimal settings inside of each GPO and then have many more GPOs as opposed to one GPO that contains all the 
settings?
  - Changing more than one setting per GPO allows for more confusion, and forgetting some settings that might've been changed. Minimal setting changes allow changes in administation to know what policies do what.
7. Describe the purpose of the commands gpupdate and gpresult.
  - the gpupdate command gets the latest group policy changes from the server.
  - the gpresult command tells the user whether or not the changes were successfully applied. It also displays the whole list of current settings that are now applied to the user and/or computer.
8. What might be an example where you would block GPO inheritance?
  - Teachers that are part of a specific student group have special permissions to oversee what the students are doing.
9. How does enforcing GPOs affect GPO precedence?
  - Enforced GPOs are applied first followed by the non-enforced, from the top of the tree to the branches.
10. Why might you want to disable all User Configuration settings in a GPO?
  - It reduces the redunancy of checking the same policy settings in other GPOs.
11. When testing a new GPO why might you want to filter it to an individual user or computer?
  - Testing it on a single computer allows only one user to be affected. If a policy doesn't behave as expected, it doesn't slow down the entire organization.
12. Why is it “dangerous” to block a GPO by using the Deny permission in the Delegation tab?
  - It doesn't show that the user is denied even if they are still receiving those group policies. This is a setting that would be easy to forget.
13. What are some examples of using WMI filters for GPO filtering?
  - Filtering Laptops and tablets apart from Desktops
  - Time of day (east coast vs west coast for example)
  - Operating system type.

**References:**
  - https://www.safaribooksonline.com/library/view/mastering-windows-group/9781789347395/?orpq
  - http://virtuallystable.com/2018/05/18/group-policy-wmi-filtering/

**Conclusion:**
This lab provided a basic overview of how policies work on a network. There are lots of options, and it can easily become complicated if policies aren't documented or sorted in a reasonable manner. Major hiccups in this lab included being locked out (policy) and improper client structure leading to improper policy application. Overall, it covered the necessities, and was a good learning experience.
