 ![](RackMultipart20200513-4-110rpn_html_42459b3d907a449a.jpg)

**OHTS ASSIGNMENT**

A.G.Malanga Mishad Vishwajith Thilakarathna.

IT16035836

BSc (Hons) in Information Technology Specializing in Cyber Security

Department of Information Technology

Sri Lanka Institute of Information Technology

Sri Lanka

MAY 2020

# Table of Contents

[WHAT IS SUDO? 3](#_Toc40291222)

[SUDORE FILE 3](#_Toc40291223)

[How to setup attack 3](#_Toc40291224)

[Vulnerability details 4](#_Toc40291225)

[Brief description of vulnerability 4](#_Toc40291226)

[DEMONSTRATION OF EXPLOTING THE VULNERABILITY 5](#_Toc40291227)

[REFERENCES 13](#_Toc40291228)

[Figure 1: the command to check the sudo version 1](/A:%5Cmalanga%5C4th%20yr%5Creport%20figures.docx#_Toc40268031)

[Figure 2: checking the passwd file: command 2](/A:%5Cmalanga%5C4th%20yr%5Creport%20figures.docx#_Toc40268032)

[Figure 3: shows the password file 2](/A:%5Cmalanga%5C4th%20yr%5Creport%20figures.docx#_Toc40268033)

[Figure 4: hash file 3](/A:%5Cmalanga%5C4th%20yr%5Creport%20figures.docx#_Toc40268034)

[Figure 5: hash values 3](/A:%5Cmalanga%5C4th%20yr%5Creport%20figures.docx#_Toc40268035)

[Figure 6: making a new user 4](/A:%5Cmalanga%5C4th%20yr%5Creport%20figures.docx#_Toc40268036)

[Figure 7: user will get a password 5](/A:%5Cmalanga%5C4th%20yr%5Creport%20figures.docx#_Toc40268037)

[Figure 8: user ID checking 5](/A:%5Cmalanga%5C4th%20yr%5Creport%20figures.docx#_Toc40268038)

[Figure 9: accessing sudo&#39;s file 6](/A:%5Cmalanga%5C4th%20yr%5Creport%20figures.docx#_Toc40268039)

[Figure 10: user privileges 7](/A:%5Cmalanga%5C4th%20yr%5Creport%20figures.docx#_Toc40268040)

[Figure 11: ID command user privilege denied 7](/A:%5Cmalanga%5C4th%20yr%5Creport%20figures.docx#_Toc40268041)

[Figure 12: sudo command user privilege denied 8](/A:%5Cmalanga%5C4th%20yr%5Creport%20figures.docx#_Toc40268042)

[Figure 13: root user ID 9](/A:%5Cmalanga%5C4th%20yr%5Creport%20figures.docx#_Toc40268043)

[Figure 14: exploiting vulnerability 9](/A:%5Cmalanga%5C4th%20yr%5Creport%20figures.docx#_Toc40268044)

# WHAT IS SUDO?

Sudo, abbreviated for Super User Do, is a program for UNIX and Linux systems that gives the user the permissions needed to run commands and scripts as the root of the system and logs all the commands and arguments. A sudo system administrator can:

- Give permissions for users to run root commands of the system operation
- Control the commands a user can use of each host
- See the commands used by the users via a log
- Control the time duration given for each user to enter commands after logging through the use of timestamp files

# SUDORE FILE

This is a file located at /etc/sudoers which controls the sudo command privileges within users, which includes elevated privileges. The best and safest way to edit this is by using the visudo command. This command allows you to edit and save the file by using vi editor. This will also put a filelock on the file to prevent other users from editing it. Once editing is done, it will parse the file for simple errors [2]

## How to setup attack

1. Download Ubuntu 16.4 from a secure website, most commonly used is oxboxes.org [3]
2. Install virtual box from the website
3. Open virtual box and add a new machine
4. Give a name to your virtual machine
5. Set the file path to the image
6. Give type as linux
7. Set version as your downloaded file whether 64bit or 32bit
8. Set RAM size and create

## Vulnerability details

- Release date: 14th October 2019
- CVE ID: CVE-2019-14287
- Affected Versions: Versions prior to \&lt;= 1.8.28
- [**https://www.sudo.ws/alerts/minus\_1\_uid.html**](https://www.sudo.ws/alerts/minus_1_uid.html)

# Brief description of vulnerability

Even though user permissions in the sudoer file mentions that it explicitly prevents users running commands as root, the security bypass vulnerability allows the users with Linux systems to execute commands as root.

A user which as ALL permissions in the Runas specifications can execute these commands on any or all the users of the system.

This vulnerability allows the users to specify their user ID as -1 or the unsigned equivalent of -1: 4294967295 and this allows the users to run commands and tools as root.

sudo -u#-1 /usr/bin/id or the unsigned equivalent of -1 sudo -u#4294967295 /usr/bin/id

# DEMONSTRATION OF EXPLOTING THE VULNERABILITY

![](RackMultipart20200513-4-110rpn_html_f41f8e0abf9953c2.png)

_Figure 1: the command to check the sudo version_

- This demonstrates the command to check the sudo version.
- This shows that the sudo versions affected are version 1.8.16 and earlier.

![](RackMultipart20200513-4-110rpn_html_3cafa38554c7fe05.png)

_Figure 2: checking the passwd file: command_

- In linux systems there is a separate file for passwords. The command to check this password file is cat/etc/passwd. The password that is stored in the file is denoted with a letter X

![](RackMultipart20200513-4-110rpn_html_dc91d231099fac80.png)

_Figure 3: shows the password file_

![](RackMultipart20200513-4-110rpn_html_1c7c551ee0e93ef7.png)

![](RackMultipart20200513-4-110rpn_html_24cd27bbe023e1d.gif)

_Figure 4: hash file_

- The hash values of the aforementioned passwords are found in the shadow file

![](RackMultipart20200513-4-110rpn_html_30aa13da251f9174.png)

_Figure 5: hash values_

- This shows the hash value of the password belonging the user called &quot;osboxes&quot;

![](RackMultipart20200513-4-110rpn_html_2cbdbc0bccfa5bf6.png)

_Figure 6: making a new user_

- To make the attack demonstration easier, I will be making a new user.
- s /bin/bash ohtsassignment

![](RackMultipart20200513-4-110rpn_html_39902bde76a38697.png)

_Figure 7: user will get a password_

_Figure 8: user ID checking_

- ![](RackMultipart20200513-4-110rpn_html_e54b4eed1e22fa2b.png)The password file will be rechecked, and we can then notice that the user id has been increased by 1. In the linux system there are 2 user ID assigning methods. The System users will get user IDs greater than 0 less than 1000, and the user accounts will get greater than 1000. The user ID of the root will always be 0.

![](RackMultipart20200513-4-110rpn_html_83a65f34cfbee6be.png)

![](RackMultipart20200513-4-110rpn_html_752e71ba2de07f98.gif)

_Figure 9: accessing sudo&#39;s file_

- We are now going to access sudo&#39;s file. The command is as follows:

_Figure 10: user privileges_

![](RackMultipart20200513-4-110rpn_html_c91536649639d754.png)Vsudo vipsudo

- Inside sudo&#39;s file you can find user privileges, the commands that the users can and can&#39;t use

![](RackMultipart20200513-4-110rpn_html_124c938dae26c038.png)

![](RackMultipart20200513-4-110rpn_html_4306dc803f81b574.gif)

_Figure 11: ID command user privilege denied_

- The new privilege for user named ohts assignment to execute the ID command will be removed

![](RackMultipart20200513-4-110rpn_html_dd1037efcb49e8f6.png)

![](RackMultipart20200513-4-110rpn_html_f03e40501dc96f0d.gif)

_Figure 12: sudo command user privilege denied_

- It is now demonstrated that even if the ohts user executes the sudo commands, it will be denied

 ![](RackMultipart20200513-4-110rpn_html_3e0dcb1d94567193.gif)

_Figure 13: root user ID_

- ![](RackMultipart20200513-4-110rpn_html_688056ded996447.png)The user ID of the user named OHTS assignment is 10001. The user ID of root is zero. Even if the use the root and try to run the ID command, it will be denied

![](RackMultipart20200513-4-110rpn_html_4ae1096b1d1a8cd3.png)

![](RackMultipart20200513-4-110rpn_html_700820aaa8458bed.gif)

_Figure 14: exploiting vulnerability_

- I will now exploit this vulnerability. I will now be using user ID -1, which will bypass and give me access to all privileged. Accordingly, I can run the commands run denied to user ohts assignment by using the user id as -1

# REFERENCES

1. [https://searchsecurity.techtarget.com/definition/sudo-superuser-do](https://searchsecurity.techtarget.com/definition/sudo-superuser-do)
2. [https://linuxacademy.com/blog/linux/linux-commands-for-beginners-sudo/](https://linuxacademy.com/blog/linux/linux-commands-for-beginners-sudo/)
3. [https://www.osboxes.org/ubuntu/](https://www.osboxes.org/ubuntu/)
4. [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)
