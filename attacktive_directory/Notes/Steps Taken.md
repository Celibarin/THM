# Proving Grounds - "Machine Name" - 192.168.x.x

# Enumeration
## Nmap
### Inital Scan
Command
```
nmap -A -vv -oA enum/nmap-initial 192.168.
```

Output
```
PORT     STATE SERVICE       REASON  VERSION                                                                                                                                                                                                 
53/tcp   open  domain        syn-ack Simple DNS Plus                                                                                                                                                                                         
80/tcp   open  http          syn-ack Microsoft IIS httpd 10.0                                                                                                                                                                                
|_http-server-header: Microsoft-IIS/10.0                                                                                                                                                                                                     
|_http-title: IIS Windows Server                                                                                                                                                                                                             
| http-methods:                                                                                                                                                                                                                              
|   Supported Methods: OPTIONS TRACE GET HEAD POST                                                                                                                                                                                           
|_  Potentially risky methods: TRACE                                                                                                                                                                                                         
88/tcp   open  kerberos-sec  syn-ack Microsoft Windows Kerberos (server time: 2022-01-06 23:59:10Z)                                                                                                                                          
135/tcp  open  msrpc         syn-ack Microsoft Windows RPC                                                                                                                                                                                   
139/tcp  open  netbios-ssn   syn-ack Microsoft Windows netbios-ssn                                                                                                                                                                           
389/tcp  open  ldap          syn-ack Microsoft Windows Active Directory LDAP (Domain: spookysec.local0., Site: Default-First-Site-Name)                                                                                                      
445/tcp  open  microsoft-ds? syn-ack                                                                                                                                                                                                         
464/tcp  open  kpasswd5?     syn-ack                                                                                                                                                                                                         
593/tcp  open  ncacn_http    syn-ack Microsoft Windows RPC over HTTP 1.0                                                                                                                                                                     
636/tcp  open  tcpwrapped    syn-ack                                                                                                                                                                                                         
3268/tcp open  ldap          syn-ack Microsoft Windows Active Directory LDAP (Domain: spookysec.local0., Site: Default-First-Site-Name)                                                                                                      
3269/tcp open  tcpwrapped    syn-ack                                                                                                                                                                                                         
3389/tcp open  ms-wbt-server syn-ack Microsoft Terminal Services                                                                                                                                                                             
|_ssl-date: 2022-01-06T23:59:27+00:00; 0s from scanner time.                                                                                                                                                                                 
| rdp-ntlm-info:                                                                                                                                                                                                                             
|   Target_Name: THM-AD                                                                                                                                                                                                                      
|   NetBIOS_Domain_Name: THM-AD                                                                                                                                                                                                              
|   NetBIOS_Computer_Name: ATTACKTIVEDIREC                                                                                                                                                                                                   
|   DNS_Domain_Name: spookysec.local                                                                                                                                                                                                         
|   DNS_Computer_Name: AttacktiveDirectory.spookysec.local                                                                                                                                                                                   
|   Product_Version: 10.0.17763                                                                                                                                                                                                              
|_  System_Time: 2022-01-06T23:59:16+00:00                                                                                                                                                                                                   
| ssl-cert: Subject: commonName=AttacktiveDirectory.spookysec.local                                                                                                                                                                          
| Issuer: commonName=AttacktiveDirectory.spookysec.local
| Public Key type: rsa
| Public Key bits: 2048
| Signature Algorithm: sha256WithRSAEncryption
| Not valid before: 2022-01-05T23:57:54
| Not valid after:  2022-07-07T23:57:54
| MD5:   acf9 4b46 4cfe 8555 c070 b863 f8d1 1765
| SHA-1: 5542 15f0 740c 8ce5 29ff c67d 8a83 3a98 a9f8 f252
| -----BEGIN CERTIFICATE-----
| -----BEGIN CERTIFICATE-----
| MIIDCjCCAfKgAwIBAgIQKfggNnNu95JGvk/TOOaS5TANBgkqhkiG9w0BAQsFADAu
| MSwwKgYDVQQDEyNBdHRhY2t0aXZlRGlyZWN0b3J5LnNwb29reXNlYy5sb2NhbDAe
| Fw0yMjAxMDUyMzU3NTRaFw0yMjA3MDcyMzU3NTRaMC4xLDAqBgNVBAMTI0F0dGFj
| a3RpdmVEaXJlY3Rvcnkuc3Bvb2t5c2VjLmxvY2FsMIIBIjANBgkqhkiG9w0BAQEF
| AAOCAQ8AMIIBCgKCAQEAxLog3wce3OlkBZb+oi8RimDlUfwIry+fBeUk4dEazGvv
| OtJOJk8vQQ1Fpi7cf02QTvfYColCFXEmFkVF6r/5LXEPXGgTdRLhQaeJsuuukNSY
| PYtdO1oZK0suX/2TniVF2rCaQKyvaaTN6HrChvZopVxTaXqsKP2wtQlPKAIapcPD
| 2rNGYWA5E6eSr7HimVtmThGiMba61fCWvIEoZeBfqlua9tCMgB4b4OVKmSfbIEs+
| lf/XM8TAxLF3YoyCffKiW9loIRDZsgSNq1Ac8URqGmlbDitoKR7gIGuN+w3WyMlX
| 7LUhdaY96MQnH3pWyUiUlddbbStsBu2PSuIVSt3YdQIDAQABoyQwIjATBgNVHSUE
| DDAKBggrBgEFBQcDATALBgNVHQ8EBAMCBDAwDQYJKoZIhvcNAQELBQADggEBAJcS
| OLIuKNYU6n9WyjNltJrb/NlSov8Q2jPKkacbCypQMy45OR/+zQNYxhmjGlGygFSf
| 0asp7ZC1g8xLGU9hRXCyt7TTo7ecAaKFOI8WW3qL2astXfdlCvva1Bd1vBavn1I8
| ruzIE1JKItPqMegpoOaIq+nlV+OU88eLMh6Vyg1fWwWgGLqoW3flzn1UYzGMJoHJ
| 30q1HrYzHHdlTRIhAgyKm4OemJ6BneXEW9kfbXc0ivPrFZtI835ABNXhlmAFiUSm
| 3puE8jKAccTdclLzuyyDa2JcVapwH7Zhinn1irNH3oqRnWWW2Ac8LaK2/s5gfEG4
| Kh1pLv6dqEa3jLVAMNQ=
|_-----END CERTIFICATE-----
Service Info: Host: ATTACKTIVEDIREC; OS: Windows; CPE: cpe:/o:microsoft:windows
```

### Full Scan
Command
```
nmap -A -vv -p- -oA enum/nmap-full 192.168.
```

Output
```

```

## Port 80
### Nikto
Command
```
nikto -h http://192.168. -o enum/nikto.txt
```

Output
```

```

### GoBuster
Command
```
gobuster dir -u http://192.168. -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -o enum/gobuster.txt
```

Output
```

```
 
---

# Vulnerabilities


---

# Privilege Escalation


---

# Loot
## User
Command
```
ifconfig;id;hostname;cat local.txt
```
>

## Root/Admin
Command
```
ifconfig;id;hostname;cat proof.txt
```
>