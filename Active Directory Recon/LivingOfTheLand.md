# Get all domain users
* net users /domain


Get Usernames and decription field
* Get-WmiObject Win32_UserAccount -filter {LocalAccount="False" and disabled ="False"} | select-object caption,description
Same as above put write to csv
* Get-WmiObject Win32_UserAccount -filter {LocalAccount="False" and disabled ="False"} | select-object caption,description | Export-csv users.csv

# Get password policy
* net accounts /domain

# Get all domain groups
* net groups /domain

# Get members of domain group
* net groups \<group name\> /domain
  
