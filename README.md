<h1>PowerShell - Bulk User Account Creation-Modification</h1>

 User Account Creation & Modification using PowerShell

<h2>Description</h2>
This documentation describes how to create and manipulate CSV files for use with PowerShell scripts in an Active Directory environment. You will have gained experience with using spreadsheet programs, such as Microsoft Excel or Google Sheets, to create and organize data in a CSV file. This document will also explain how to import this data into a PowerShell script and use it to perform tasks such as creating new user accounts, modifying existing user accounts, and disabling or removing user accounts that are no longer needed. Additionally, you will have learned how to properly format a CSV file to match the requirements of a specific PowerShell script, and how to troubleshoot any formatting errors that may occur. Additionally, you will learn how to use PowerShell cmdlets to perform user provisioning, maintenance, and de-provisioning tasks and how to handle errors and feedbacks.
<br />
<br /> 

<br />


<h2>Tools, Languages, and Utilities Used</h2>

- <b>PowerShell</b> 
- <b>Spreadsheet program: Excel or Google Sheets, for creating and editing the CSV files.</b>
- <b>Active Directory</b>
- <b>CSV (Comma Separated Values) format</b>

<h2>Environments Used </h2>

- <b>VirtualBox</b>
- <b>Windows 10</b> (21H2)
- <b>Windows Server</b>

<h2>Creating the CSV file needed to complete the walk through:</h2>

 1.	Open a blank document in a spreadsheet program, such as Microsoft Excel or Google Sheets
 2.	In the first row of the spreadsheet, enter the names of the columns that you want to include in your CSV file. For example, if you are creating a file to store information about users, you might include columns for the user's name, email address, and telephone number.
3.	In the rows below the column headers, enter the data that you want to include in your CSV file. Be sure to enter the data in the correct columns, so that it corresponds to the appropriate column headers.
4.	Once you have entered all the data that you want to include in your CSV file, go to File -> Save As.
5.	In the "Save As" dialog box, select "CSV" as the file format.
6.	Give the file a meaningful name, like "Users.csv" and choose a location to save it.
7.	Click the Save button, your CSV file has been created.
8.	You can now use this CSV file in conjunction with a PowerShell script to import the data and perform actions on it.

It's important to note that the structure of your CSV file will depend on the requirements of the script you are using it with, so be sure to check the documentation of the script to see what columns it expects and what format the data should be in. Also, be careful with the formatting of the data to avoid errors when running the script.

 

<h2>Step-by-step walk through guide:</h2>

<p align="left">

Here is a step-by-step tutorial that covers Automating user account provisioning, maintenance, and de-provisioning:

 1.	<b>Creating a CSV file:</b> 1.	Create a CSV file with the following columns: Name, SamAccountName, GivenName, Surname, Password, and Group.

 2.	<b>2.	Fill the CSV file with the users' information:</b>
 <br/>
 3.	<b>Open PowerShell and run the following script:</b>
 <br />
<img src="https://i.imgur.com/WUr0ASF.jpg" height="80%" width="80%"/>
<br />
<br />
 This script will read the CSV file, create new AD user objects using the <b>New-ADUser</b> cmdlet, set the user's account as enabled, and set a flag to require the user to change the password at first login. It will also add the user to the specified group using the <b>Add-ADGroupMember</b> cmdlet and display a message indicating that the user has been created and added to the group.
<br />
<br />
 3.	<b>Modifying existing user accounts:</b> 
 <br />
 1.	Create a CSV file with the following columns: SamAccountName, NewGivenName, NewSurnamen
 <br />
 2.	Fill in the CSV file with the users' new information.
 <br />
 3.	Open PowerShell and run the following script:
  <br/>
<img src="https://i.imgur.com/aupHlWV.jpg" height="80%" width="80%"/>
 <br />
<br />
This script will read the CSV file, update the user object attributes using the <b>Set-ADUser</b> cmdlet, and display a message indicating that the user has been modified with the new name.
<br />
<br />
 4.	<b>Removing or disabling user accounts that are no longer needed:</b>
 <br /> 
 1.	Create a CSV file with the following column: SamAccountName
 <br />
 2.	Fill the CSV file with the users' SamAccountName to disable.
 <br />
 3.	Open PowerShell and run the following script:
 <br/>
<img src="https://imgur.com/77BkcXr.jpg" height="80%" width="80%"/>
<br />
<br />
 This function takes in the file path as a parameter and uses the <b>Send-MailMessage</b> cmdlet to send an email alert to the specified email address.
<br />
<br />
 <img src="https://i.imgur.com/T7KLXLK.jpg" height="80%" width="80%"/>
 <br/>
This script will read the CSV file, iterate through each row, and execute the command <b>Disable-ADAccount -Identity $User.SamAccountName</b>, which will disable the user account, identified by its SamAccountName, in the Active Directory. It will also print out the message "User $($User.Name) has been disabled." using the <b>Write-Host</b> cmdlet, to indicate that the user account has been successfully disabled.
<br />
<br />
It's important to note that disabling an account is a safer option than deleting an account, as it prevents the user from logging in to the domain, but still leaves the account in AD, in case you need to enable it again. Additionally, it's good practice to back up your AD before running any script that modifies it, in case something goes wrong.
<br />
<br />
Also, you can adjust the script to check if the user exists before disabling it, to avoid errors
<br />
  <br/>
<img src="https://i.imgur.com/54zAJ15.jpg" height="80%" width="80%"/>
<br />
<br />
  <br/>

</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
