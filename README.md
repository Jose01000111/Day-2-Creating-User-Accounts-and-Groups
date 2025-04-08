<p align="center">
<img src="https://i.imgur.com/pqTjnLb.png" alt="osTicket logo"/>
</p>

## Day 2 – Creating User Accounts and Security Groups

With the domain live, I received a staff list from HR and was responsible for ensuring all users would be able to access systems and data on day one—without permission overlap or security gaps.

Using a CSV file and PowerShell, I bulk-created user accounts, assigned them to role-based security groups, and configured password policies. (Used ChatGPT to script validation and group logic.)



### 🛠️ Day 2: Creating User Accounts and Groups for Initial Staff:

### 🧪 Lab Tasks

•	Create user accounts from a CSV file for employees.

•	Assign users to security groups (e.g., Admin, HR, IT, Operations).

•	Set up password policies and force users to change passwords upon first login.

#### 1. Prepare the CSV File for User Information 📄
•	Create a CSV file with columns for:

 o	First Name

 o	Last Name

 o	Username

 o	Password

 o	Department

 <p align="center">
<img src="https://i.imgur.com/v7bB2Wb.png" alt="osTicket logo"/>
</p>

 •	Example data should include details for users in different departments such as Admin, HR, IT, Operations, and a special entry for "Staley the Bear" in the Mascot department.

<p align="center">
<img src="https://i.imgur.com/dC6Ll1R.png" alt="osTicket logo"/>
</p>

 •	Save this file as users.csv in an easily accessible location on your server.

#### 2. Create User Accounts in Active Directory 🖥️

 •	Open Active Directory Users and Computers (ADUC) on your server.

 •	For each user:

1.	Right-click the relevant Organizational Unit (OU) (e.g., Admin, HR, IT, Operations, or Mascot).

2.	Select New > User.

3.	Fill out the user details (First Name, Last Name, Username, Password).

4.	Uncheck User must change password at next logon (we'll configure this later).

5.	Click Finish to create the user.
   
6.	Repeat for all users (John, Jane, Bob, Alice, and Staley).

#### 3. Assign Users to Security Groups 🔑

 •	For each user, assign them to their respective security group based on their department.

1.	In ADUC, right-click the user account.

2.	Select Properties.

3.	Go to the Member Of tab.

Click Add, search for the relevant group (e.g., Admin, HR, IT, Operations, Mascot), and click OK.

<p align="center">
<img src="https://i.imgur.com/2Gn3F6E.png" alt="osTicket logo"/>
</p>

•	Ensure each user is placed in the correct security group:

 o	jdoe → Admin Group

 o	jsmith → HR Group

 o	bjohnson → IT Group

 o	awilliams → Operations Group

 o	staley → Mascot Group

#### 4. Set Up Password Policies 🔐

•	Open Group Policy Management.

<p align="center">
<img src="https://i.imgur.com/7Zv6O8F.png" alt="osTicket logo"/>
</p>

•	Right-click your domain and select Create a GPO in this domain, and Link it here.

•	Name the new GPO (e.g., Password Policy) and click OK.

<p align="center">
<img src="https://i.imgur.com/HI53KW8.png" alt="osTicket logo"/>
</p>

•	Right-click the new GPO and select Edit.

•	Navigate to Computer Configuration > Policies > Windows Settings > Security Settings > Account Policies > Password Policy.

•	Set the following policies:

 o	Minimum password length: 8 characters

 o	Password must meet complexity requirements: Enabled

 o	Maximum password age: 60 days

 o	Minimum password age: 1 day

 https://imgur.com/yBVsdmT

•	Close the Group Policy Management console.

#### 5. Force Users to Change Passwords Upon First Login 🔄

<p align="center">
<img src="https://i.imgur.com/szCfLca.png" alt="osTicket logo"/>
</p>

<p align="center">
<img src="https://i.imgur.com/LIC6ibW.png" alt="osTicket logo"/>
</p>

•	Open Active Directory Users and Computers (ADUC).

•	For each user:

1.	Right-click the user account and select Properties.

2.	Under the Account tab, check the box for User must change password at next logon.

<p align="center">
<img src="https://i.imgur.com/weGbB91.png" alt="osTicket logo"/>
</p>   

3.	Click OK to apply the change.

#### 6. Verify User Account Creation and Group Membership ✅

•	Open Active Directory Users and Computers (ADUC).

•	Navigate to each Organizational Unit (OU) (Admin, HR, IT, Operations, Mascot).

 1.	User accounts are listed in their respective OUs (e.g., jdoe in Admin, jsmith in HR).
   
 3.	Each user is a member of the correct security group (e.g., jdoe in Admin, jsmith in HR).
   
•	To verify group membership:

 1.	Right-click a user account and select Properties.
   
 3.	Go to the Member Of tab to ensure they are in the correct group.

### Technology Stack 🛠️
#### Active Directory: Manage user accounts and security groups.

#### CSV Files: Store user details for bulk import.

#### Group Policy Management: Set password policies.

#### Windows Server: Host Active Directory and Group Policy tools.

#### osTicket: Brand/logo for ticket management.

### Summary of Goals 🎯
#### ✅Create user accounts from a CSV file.

#### ✅Assign users to the correct security groups.

#### ✅Configure password policies for secure logins.

#### ✅Force users to change their passwords upon first login.

#### ✅Verify user account creation and group membership.
