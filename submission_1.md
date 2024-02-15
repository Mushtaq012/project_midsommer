# Weak Password Authentication and Brute Force Vulnerability

**Severity : Critical**

# Description
During a scan, the WordPress - wp-login page was accessible from any IP address, exposing the login page to any user. After further scanning was able to identify the login page is vulnerable to weak password authentication and suspectibility to  brute force attacks on the login page. This can lead to unauthorized access posing a risk to data security and the overall system integrity.
 
## Overview of the Vulnerability
An attacker could exploit this vulnerability by performing Brute Force attacks on users or by creating a similar phishing website in order to obtain admin and user credentials, as anybody can access the login page.
## Affected Target
Website Login Page : http://13.127.206.195:31337/wp-login.php

## Risk Rating
Risk: Critical
Difficulty to Exploit : Low

## Proof of Concept
A proof of concept for a brute-force assault was constructed on the wp-login page, and the admin page was successfully reached, as demonstrated below.

**Step 1**
Navigate to http://13.127.206.195:31337/wp-login.php 

**Step 2**
To identify the username tested with some common usernames until the WordPress login screen prompts the correct username with an error message.
<a href="https://ibb.co/BC68Vcg"><img src="https://i.ibb.co/87xFDNj/Screenshot-8.png" alt="Screenshot-8" border="0"></a>

**Step 3**
After identifying the username,
Perfomed a brute-force attack on the password field with some common password lists.

<a href="https://ibb.co/cbqWhT7"><img src="https://i.ibb.co/4skbRN5/Screenshot-10.png" alt="Screenshot-10" border="0"></a>
<a href="https://ibb.co/QMTb14H"><img src="https://i.ibb.co/pdM09SK/Screenshot-9.png" alt="Screenshot-9" border="0"></a>
<a href="https://ibb.co/nDqwSkg"><img src="https://i.ibb.co/fCVX701/Screenshot-11.png" alt="Screenshot-11" border="0"></a>
<a href="https://ibb.co/42T8hsd"><img src="https://i.ibb.co/1MqrFs6/Screenshot-12.png" alt="Screenshot-12" border="0"></a>
<a href="https://ibb.co/mycpVyR"><img src="https://i.ibb.co/2MkJ1MF/Screenshot-13.png" alt="Screenshot-13" border="0"></a>
<a href="https://ibb.co/g6bZmQF"><img src="https://i.ibb.co/mSr5bdF/Screenshot-15.png" alt="Screenshot-15" border="0"></a>
<a href="https://ibb.co/rFCPRRF"><img src="https://i.ibb.co/34DX994/Screenshot-16.png" alt="Screenshot-16" border="0"></a>

## Business Impact
Due to lack of weak password authentication any user can use a brute force attack to exploit the login page, resulting in website alteration and modification. This can cause reputational damage to the business and compromise of user accounts and data security. Which leads to unauthorized access and potential misuse of sensitive information.


## Recommendation

 - Implement strong password policies
 - Rate Limiting 
 - User education
 
## References

 - https://www.fortinet.com/resources/cyberglossary/brute-force-attack#:~:text=The%20attacker%20starts%20with%20a,SanDiego123%22%20or%20%22Rover2020.%22

 - https://www.acunetix.com/vulnerabilities/web/weak-password/#:~:text=A%20weak%20password%20is%20short,common%20variations%20on%20these%20themes.

