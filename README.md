# configure-ad


<p>
VERY END, SETTING A GROUP POLICY.
Now to configure account lockout policy via group policy. First open group policy management console (GPMC) on the dc-1 VM. (Right click the start button -> click "run" -> type gpmc.msc -> enter. 
Right click "mydomain.com" the domain we created, where we want to apply the policy, and click edit. 
Navigate to the account lockout policy settings. Computer Configuration -> Policies -> Windows Settings -> Security Settings -> Account Policies -> Account Lockout Policy.
Now the settings are visible and can be set. Set the account lockout duration to 30 minutes, the lockout threshold to 5 attempts, and reseet account lockout counter after 10 minutes. 
Insert the AccLock-image1 and 2 here.
<p>
<img width="728" alt="image" src="https://github.com/user-attachments/assets/51957803-4e27-48a2-9545-db88f5379e0a" />
</p>

Now for the new settings to apply, we can wait for the group policy to propogate automatically, or we can force an update immediately. 
On a client machine, open commmand prompt and type gpupdate /force, then press enter. So we will login into client-1 VM as the admin (mydoman.com\jane_admin). 
Insert AccLock-image3 here.

To check if the group policy is in place, log out of the admin account and try to login as user and incorrectly enter the password 5 times. I used mydomain.com\bagom.mikul and an incorrect password. 
The account was locked after 5 attempts, the group policy is working.
Insert AccLock-image4.

Now we can go and unlock the account, back in dc-1 VM, go to the Active Directory Users and Computers -> mydomain.com -> right click _EMPLOYEES -> Find -> Type the user account you locked out (bagon.mikul) -> double click the account -> check Unlock Account.
bagom.mikul is now unlocked.
If we wanted to reset the password of the same account we could go into Active Directory Users and Computers, right click the account -> click Reset Password...
Insert Accock-image5


</p>
