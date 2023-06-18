# CVE-2023-20178

This is PoC for Arbitrary File Delete vulnerability in Cisco Secure Client (tested on 5.0.01242) and Cisco AnyConnect  (tested on 4.10.06079).

![poc](https://github.com/Wh04m1001/CVE-2023-20178/assets/44291883/f64f2b03-3045-4b37-91a2-508b24aea2f9)

When a user connect to vpn, vpndownloader.exe process is started in background and it will create directory in c:\windows\temp with default permissions in following format:
<random numbers\>.tmp 
After creating this directory vpndownloader.exe will check if that directory is empty and if its not it will delete all files/directories in there.
This behaviour can be abused to perform arbitrary file delete as NT Authority\SYSTEM account.

Arbitrary file delete is then used to spwan system cmd process by abusing windows installer behaviour which is described in ZDI article https://www.zerodayinitiative.com/blog/2022/3/16/abusing-arbitrary-file-deletes-to-escalate-privilege-and-other-great-tricks (discovered by @KLINIX5)

# Advisory 
  
https://sec.cloudapps.cisco.com/security/center/content/CiscoSecurityAdvisory/cisco-sa-ac-csc-privesc-wx4U4Kw
