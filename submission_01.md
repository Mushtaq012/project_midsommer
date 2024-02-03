---


---

<h1 id="weak-password-authentication-and-brute-force-vulnerability">Weak Password Authentication and Brute Force Vulnerability</h1>
<p><strong>Severity : Critical</strong></p>
<h1 id="description">Description</h1>
<p>During a scan, the WordPress - wp-login page was accessible from any IP address, exposing the login page to any user. After further scanning was able to identify the login page is vulnerable to weak password authentication and suspectibility to  brute force attacks on the login page. This can lead to unauthorized access posing a risk to data security and the overall system integrity.</p>
<h2 id="overview-of-the-vulnerability">Overview of the Vulnerability</h2>
<p>An attacker could exploit this vulnerability by performing Brute Force attacks on users or by creating a similar phishing website in order to obtain admin and user credentials, as anybody can access the login page.</p>
<h2 id="affected-target">Affected Target</h2>
<p>Website Login Page : <a href="http://13.127.206.195:31337/wp-login.php">http://13.127.206.195:31337/wp-login.php</a></p>
<h2 id="risk-rating">Risk Rating</h2>
<p>Risk: Critical<br>
Difficulty to Exploit : Low</p>
<h2 id="proof-of-concept">Proof of Concept</h2>
<p>A proof of concept for a brute-force assault was constructed on the wp-login page, and the admin page was successfully reached, as demonstrated below.</p>
<p><strong>Step 1</strong><br>
Navigate to <a href="http://13.127.206.195:31337/wp-login.php">http://13.127.206.195:31337/wp-login.php</a></p>
<p><strong>Step 2</strong><br>
To identify the username tested with some common usernames until the WordPress login screen prompts the correct username with an error message.<br>
<a href="https://ibb.co/BC68Vcg"><img src="https://i.ibb.co/87xFDNj/Screenshot-8.png" alt="Screenshot-8" border="0"></a></p>
<p><strong>Step 3</strong><br>
After identifying the username,<br>
Perfomed a brute-force attack on the password field with some common password lists.</p>
<p><a href="https://ibb.co/cbqWhT7"><img src="https://i.ibb.co/4skbRN5/Screenshot-10.png" alt="Screenshot-10" border="0"></a><br>
<a href="https://ibb.co/QMTb14H"><img src="https://i.ibb.co/pdM09SK/Screenshot-9.png" alt="Screenshot-9" border="0"></a><br>
<a href="https://ibb.co/nDqwSkg"><img src="https://i.ibb.co/fCVX701/Screenshot-11.png" alt="Screenshot-11" border="0"></a><br>
<a href="https://ibb.co/42T8hsd"><img src="https://i.ibb.co/1MqrFs6/Screenshot-12.png" alt="Screenshot-12" border="0"></a><br>
<a href="https://ibb.co/mycpVyR"><img src="https://i.ibb.co/2MkJ1MF/Screenshot-13.png" alt="Screenshot-13" border="0"></a><br>
<a href="https://ibb.co/g6bZmQF"><img src="https://i.ibb.co/mSr5bdF/Screenshot-15.png" alt="Screenshot-15" border="0"></a><br>
<a href="https://ibb.co/rFCPRRF"><img src="https://i.ibb.co/34DX994/Screenshot-16.png" alt="Screenshot-16" border="0"></a></p>
<h2 id="business-impact">Business Impact</h2>
<p>Due to lack of weak password authentication any user can use a brute force attack to exploit the login page, resulting in website alteration and modification. This can cause reputational damage to the business and compromise of user accounts and data security. Which leads to unauthorized access and potential misuse of sensitive information.</p>
<h2 id="recommendation">Recommendation</h2>
<ul>
<li>Implement strong password policies</li>
<li>Rate Limiting</li>
<li>User education</li>
</ul>
<h2 id="references">References</h2>
<ul>
<li>
<p><a href="https://www.fortinet.com/resources/cyberglossary/brute-force-attack#:~:text=The%20attacker%20starts%20with%20a,SanDiego123%22%20or%20%22Rover2020.%22">https://www.fortinet.com/resources/cyberglossary/brute-force-attack#:~:text=The attacker starts with a,SanDiego123" or "Rover2020."</a></p>
</li>
<li>
<p><a href="https://www.acunetix.com/vulnerabilities/web/weak-password/#:~:text=A%20weak%20password%20is%20short,common%20variations%20on%20these%20themes">https://www.acunetix.com/vulnerabilities/web/weak-password/#:~:text=A weak password is short,common variations on these themes</a>.</p>
</li>
</ul>

