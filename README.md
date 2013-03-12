rem Set Windows License Key
rem Set Hostname
rem Set Domain
rem Restart
rem Add domain user


rem Each step writes to C:\Checkpout\InstallLog.txt if the step worked

rem Set Windows License Key -- delete 0's, keep -'s
Slmgr.vbs -ipk 00000-00000-00000-00000-00000
Slmgr.vbs -ato && echo Windows Activation Key set >> C:\Checkout\InstallLog.txt


Rem Sets the hostname of the device. Use syntax [txt]%Hostnm%[txt] for repetitive names 
wmic computersystem where name="%COMPUTERNAME%" call rename name="%Hostnm%" && echo Hostname Set >> C:\Checkout\InstallLog.txt
