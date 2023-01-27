# Manual BloodHound queries
* Find all users with the word 'password' in description.
```
MATCH (n:User) where n.description contains 'password' return n.description
```
* Find all users member of ENTERPRISE ADMINS@ACME.NO
  * MATCH (n:User)-[:MemberOf*1..]->(g:Group {name:'ENTERPRISE ADMINS@ACME.NO'}) return n.name
MATCH (c:Computer ) return c.name
MATCH (n:Group) WHERE n.objectid =~ "(?i)S-1-5-21-.*-512" WITH n MATCH p=(n)<-[r:MemberOf*1..]-(m) RETURN n.name,m.enabled,m.name


MATCH (n:User)WHERE n.enabled=true
return n.name


computers where groups are local admin
MATCH (n)-[r:AdminTo]->(c:Computer) return n.name,c.name
