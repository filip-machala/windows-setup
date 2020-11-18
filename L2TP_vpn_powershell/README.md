# Add L2TP VPN to Windows with credentials via Powershell

## Install required modules

To make this code working you need to install following modules 

```PowerShell
Install-Module -Name VPNCredentialsHelper
```
Credits: https://github.com/paulstancer/VPNCredentialsHelper

## Add connection
```PowerShell
$Name = Read-Host -Prompt "Input connection name"
$ServerAddress = Read-Host -Prompt "Input server addressg. IP or address name"
$Username = Read-Host -Prompt "Input username"
$Password = Read-Host -Prompt "Input password"
$PreSharedKey = Read-Host -Prompt "Input pre shared key"
Add-VpnConnection -Name $name -ServerAddress $address -TunnelType L2tp -EncryptionLevel Required -AuthenticationMethod MSChapv2 -L2tpPsk $presharedkey -Force:$true -RememberCredential:$true -SplitTunneling:$false
Set-VpnConnectionUsernamePassword -connectionname $name -username $username -password $plainpassword -domain ''
Write-Host "Connection added successfully." 
```

