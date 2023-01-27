# Elevate from Local admin to gMSA account

* Check if any gMSA accounts are present in the domain.
 ```powershell
Get-ADServiceAccount -Filter * -properties dnshostname
```
