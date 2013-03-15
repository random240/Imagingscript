rem Set Windows License Key
rem Set Hostname
rem Set Domain
rem Add domain user
rem Restart

Rem Each step writes to C:\Checkpout\InstallLog.txt if the step worked
echo %date% -- %time%>C:\Checkpout\InstallLog.txt

Rem Set Windows License Key -- delete 0's, keep -'s
Slmgr.vbs -ipk 00000-00000-00000-00000-00000
Slmgr.vbs -ato && echo Windows Activation Key set >> C:\Checkout\InstallLog.txt

Rem Sets the hostname of the device. Use syntax [txt]%Hostnm%[txt] for repetitive names 
wmic computersystem where name="%COMPUTERNAME%" call rename name="%Hostnm%" && echo Hostname Set >> C:\Checkout\InstallLog.txt

Rem Adds to the domain. Replace username and password with your own
NETDOM /Domain:corp.atellis.com /user:adminuser /password:apassword MEMBER MYCOMPUTER /JOINDOMAIN && echo Joined to Domain >> C:\Checkout\InstallLog.txt

Rem Adds the domain user as a local admin. Replace user.name
net localgroup administrators corp.atellis.com.local\user.name /add && echo Domain user added as admin>> C:\Checkout\InstallLog.txt
