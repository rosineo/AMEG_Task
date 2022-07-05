# AMEG_Task - ps1 scripts
You can directly run these in PowerShell. 

Disclaimer 1: From the description of the second exercise, it was not clear if it was expected to set Path and Destination (from and to) for the copy cmdlet itself or if parameters for the directory should've been set to retrieve data from a specific location. As I did not find any information on how to set dir parameters neither in the videos provided, nor in the official MS documentation, I just assumed only path and destination for the cmdlet itself are needed. 
(Also, I created the dummy file first in order to move it and the script will only work if you have directory C:\users\public. If you do not have this directory, you can create the file wherever and replace the path in the copy cmdlet.)

Disclaimer 2: I couldn't find any information for IIS Profile/s. What I found on profiles is that a profile is a script that runs when PowerShell starts, but the documentation didn't specify how it can be binded by http:
https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_profiles?view=powershell-7.2

Additionally, all the cmdlets related to New + IIS are: New-IISConfigCollectionElement, New-IISSite and New-IISSiteBinding, which also do not include profile:
https://docs.microsoft.com/en-us/powershell/module/iisadministration/?view=windowsserver2022-ps

What I was able to find instead which included binding is the following:
https://docs.microsoft.com/en-us/powershell/module/iisadministration/new-iissite?view=windowsserver2022-ps
So I ran New-IISSite and included parameter -BindingInformation. 
Also, if you're using Windows server 2012 instead of 2022 and have selected Server Role > Web Server (IIS), the cmdlet is different: 

new-website -name ‘testname’ -physicalpath ‘testpath’ -port “binding”

If you do not include port, the system defaults it to *:80:, which is also http. 
