# Lab 1 - Design Challenge

### Class: CMST 315

### 1/31/2019

### Names: Matthew Denholm, Nic Crombie, Caroline Reed

**Objective:** Our goal of this activity is to find a way to divide a block of IP addresses optimally. This will be accomplished by determining the requirements of each of the companies and then dividing the addresses into networks that will serve their needs. In the end, the result must have increased data performance (A smaller routing table size) than multiple class C Networks.

**Equipment Used:**
1. Blender (for the diagram)
2. Powerpoint
3. Pencil and Paper

**Notes and Observations:** The Initial Conditions were that a /17 block of IP addresses was given to the local ISP. This is a total of 32,768 different IP addresses that could be given out by the local ISP. The local address given was 206.12.0.0. The Four Specifications were to define Subnetworks to provide full internet access to four different companies. These comprised of networks containing 50, 200, 1500, and 5000 addresses.

An initial idea was to split the block into 8 different networks. This solution covered the vast majority of companies, except for the major ones like the ISP itself. Optimally this would be the best strategy were it not for the fact that the ISP would have two different blocks of IP addresses. This increases the routing table slightly, but it is still much more efficient than multiple class C blocks of IP addresses.

The 32K addresses were then divided into 4 different subnets. This worked better in that it allowed for the smallest routing table at the ISP, while still leaving addresses open for future growth should the ISP need it. A second subnet was divided into 4 futher sub-subnets. By doing this repetitively it could be achieved that different sized companies get different sized blocks of IPs.

One of the major notes was that each division of nodes was equal to a power of 2, and so each subdivision decided on had to include the number of nodes specified for each company. This sometimes resulted in a large waste of IP addresses as the powers of 2 are not nice rounded numbers.

**Diagrams:** See the [Design Diagram.png](https://github.com/Matthew-Denholm/Sys-Administration-Lab-Reports/blob/master/Lab%201%20-%20Design%20Challenge/Design%20Diagram.png) and [Design Diagram.mp4](https://github.com/Matthew-Denholm/Sys-Administration-Lab-Reports/blob/master/Lab%201%20-%20Design%20Challenge/Design%20Diagram0001-1216.mp4) files for appropriate documentation. Please see the [Network design.pptx](https://github.com/Matthew-Denholm/Sys-Administration-Lab-Reports/blob/master/Lab%201%20-%20Design%20Challenge/Network%20design.pptx) for presentation information.

**Conclusion:** There really wasn't a "wrong way" to do this exercise (within reason of course), as there are multiple solutions that would work depending on circumstances. The solution we went with allowed for each of the four companies to expand and grow should the need ever arise. The ISP requested 5000 nodes, and was provided a full subnet containing 8192 IP addresses. The university was given 2048 IP addresses in a request of 1500, the department store 512 for 200, and the small company was given 128 in a request for 50.

Overall, this Lab was successful, in that a solution was found for the specifications given. The trickiest part of the lab was figuring out how to divide everything up. From this lab, I learned that there is no one solution to this problem, and I also learned how VSLM (Variable Length Subnet Masking) applies to a real world situation. 
