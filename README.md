<p align="center">
<img src="https://i.imgur.com/pqTjnLb.png" alt="osTicket logo"/>
</p>

## Day 2 – Creating User Accounts and 🔒 Security Groups

With the domain live, I received a staff list from HR and was responsible for ensuring all users would be able to access systems and data on day one—without permission overlap or security gaps.

Using a CSV file and PowerShell, I bulk-created user accounts, assigned them to role-based security groups, and configured password policies. (Used ChatGPT to script validation and group logic.)

### 🧪 Lab Tasks

•	Create user accounts from a CSV file for employees.

•	Assign users to security groups (e.g., Admin, HR, IT, Operations).

•	Set up password policies and force users to change passwords upon first login.

#### 1. Prepare the CSV File for User Information 📄
I began by creating a CSV file that contains the following columns: First Name, Last Name, Username, Password, and Department. I populated the file with user data for departments like Admin, HR, IT, Operations, and a special entry for "Staley the Bear" in the Mascot department. Once completed, I saved the file as users.csv in a convenient location on my server.

 <p align="center">
<img src="https://i.imgur.com/v7bB2Wb.png" alt="osTicket logo"/>
</p>
___________________________________________________________________________________________________________

#### 2. Create User Accounts in ☁️ Active Directory 🖥️

Next, I opened Active Directory Users and Computers (ADUC) on the server. For each user, I right-clicked the relevant Organizational Unit (OU), selected New > User, and filled out the user details, such as First Name, Last Name, Username, and Password. After completing each account, I unchecked the User must change password at next logon option and clicked Finish. I repeated this process for all users.

<p align="center">
<img src="https://i.imgur.com/dC6Ll1R.png" alt="osTicket logo"/>
</p>
___________________________________________________________________________________________________________
#### 3. Assign Users to Security Groups 🔑
I then assigned each user to their respective security group based on their department. In ADUC, I right-clicked the user account, selected Properties, and went to the Member Of tab. I clicked Add, searched for the relevant group (e.g., Admin, HR, IT, Operations, Mascot), and clicked OK to assign them to the group.

<p align="center">
<img src="https://i.imgur.com/2Gn3F6E.png" alt="osTicket logo"/>
</p>

___________________________________________________________________________________________________________
#### 4. Set Up Password Policies 🔐
To set up password policies, I opened Group Policy Management and created a new Group Policy Object (GPO) named Password Policy. After linking the GPO to the domain, I navigated to Computer Configuration > Policies > Windows Settings > Security Settings > Account Policies > Password Policy. I configured the following settings: minimum password length of 8 characters, password complexity requirements enabled, maximum password age of 60 days, and a minimum password age of 1 day.

<p align="center">
<img src="https://i.imgur.com/7Zv6O8F.png" alt="osTicket logo"/>
</p>

___________________________________________________________________________________________________________

<p align="center">
<img src="https://i.imgur.com/HI53KW8.png" alt="osTicket logo"/>
</p>

___________________________________________________________________________________________________________
<p align="center">
<img src="https://i.imgur.com/yBVsdmT.png" alt="osTicket logo"/>
</p>
 https://imgur.com/yBVsdmT

___________________________________________________________________________________________________________
#### 5. Force Users to Change Passwords Upon First Login 🔄

<p align="center">
<img src="https://i.imgur.com/szCfLca.png" alt="osTicket logo"/>
</p>

___________________________________________________________________________________________________________
<p align="center">
<img src="https://i.imgur.com/LIC6ibW.png" alt="osTicket logo"/>
</p>

___________________________________________________________________________________________________________
•	Open Active Directory Users and Computers (ADUC).

•	For each user:

1.	Right-click the user account and select Properties.

2.	Under the Account tab, check the box for User must change password at next logon.

<p align="center">
<img src="https://i.imgur.com/weGbB91.png" alt="osTicket logo"/>
</p>   

___________________________________________________________________________________________________________
3.	Click OK to apply the change.

#### 6. Verify User Account Creation and Group Membership ✅

•	Open Active Directory Users and Computers (ADUC).

•	Navigate to each Organizational Unit (OU) (Admin, HR, IT, Operations, Mascot).

 1.	User accounts are listed in their respective OUs (e.g., jdoe in Admin, jsmith in HR).
   
 3.	Each user is a member of the correct security group (e.g., jdoe in Admin, jsmith in HR).
   
•	To verify group membership:

 1.	Right-click a user account and select Properties.
   
 3.	Go to the Member Of tab to ensure they are in the correct group.

___________________________________________________________________________________________________________
### 💻Technology Stack 
#### Active Directory: Manage user accounts and security groups.

#### CSV Files: Store user details for bulk import.

#### Group Policy Management: Set password policies.

#### Windows Server: Host Active Directory and Group Policy tools.

#### osTicket: Brand/logo for ticket management.

### 🎯Summary of Goals 
#### ✅Create user accounts from a CSV file.

#### ✅Assign users to the correct security groups.

#### ✅Configure password policies for secure logins.

#### ✅Force users to change their passwords upon first login.

#### ✅Verify user account creation and group membership.
