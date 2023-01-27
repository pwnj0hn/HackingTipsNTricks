# Manual BloodHound queries for use in Neo4j interface
* Find all users with the word 'password' in description.
```
MATCH (n:User) where n.description contains 'password' return n.description
```
* Find all users member of ENTERPRISE ADMINS@ACME.NO
```
MATCH (n:User)-[:MemberOf*1..]->(g:Group {name:'ENTERPRISE ADMINS@ACME.NO'}) return n.name
```
* Find all computers
```
MATCH (c:Computer ) return c.name
```
* Find all enabled members of Domain Admins
```
MATCH (n:Group) WHERE n.objectid =~ "(?i)S-1-5-21-.*-512" WITH n MATCH p=(n)<-[r:MemberOf*1..]-(m) RETURN n.name,m.enabled,m.name
```
* Find all enabled members of Domain Admins
```
MATCH (n:User)WHERE n.enabled=true return n.name
```
* Computers where users are local admin
```
MATCH (n)-[r:AdminTo]->(c:Computer) return n.name,c.name
```
