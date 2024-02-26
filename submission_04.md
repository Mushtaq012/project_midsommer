---


---

<h1 id="wordpress-plugin-translatepress-2.0.8---stored-cross-site-scripting-xss-authenticated---cve-2021-24610">WordPress Plugin TranslatePress 2.0.8 - Stored Cross-Site Scripting (XSS) (Authenticated) : # CVE-2021-24610</h1>
<p><strong>Severity : Medium</strong></p>
<h1 id="description">Description</h1>
<p>Malicious JavaScript code can be injected into the TranslatePress plugin’s database-stored settings by an authenticated user. Because of this vulnerability, an attacker can run any code within the sessions of other users, which could result in additional exploitation, data theft, or privilege escalation.</p>
<h2 id="affected-target">Affected Target</h2>
<p>This vulnerability was identified at <a href="http://43.205.237.12:31337/wp-admin/">http://43.205.237.12:31337/wp-admin/</a></p>
<h2 id="risk-rating">Risk Rating</h2>
<p>Risk: Medium<br>
Difficulty to Exploit: Low</p>
<h2 id="proof-of-concept">Proof of Concept</h2>
<p>Authentication credentials were obtained through a brute force attack.<br>
To obtain user credentials, Refer the following link:</p>
<p><a href="https://ibb.co/GcnYxYC"><img src="https://i.ibb.co/zGQ9n9P/aaaa.png" alt="aaaa" border="0"></a></p>
<p>The following steps demonstrate how to perform a XSS attack using the Plugin TranslatePress 2.0.8</p>
<p><strong>Step 1</strong></p>
<p>Obtain administrator authentication. This resulted in the page uploading potentially harmful plugins. To take use of the XSS, download TranslatePress 2.0.8 which is vulnerable to XSS. To download the TranslatePress 2.0.8 plugin, go to the exploitdb page and search for the vulnerable plugin.</p>
<p>Choose TranslatePress 2.0.8, which is required in this instance.</p>
<p><a href="https://ibb.co/jwfQV7x"><img src="https://i.ibb.co/qgjc0b4/bbbb.png" alt="bbbb" border="0"></a></p>
<p>And download it through the Vulnerable Application field.</p>
<p><a href="https://ibb.co/0998d8b"><img src="https://i.ibb.co/SmmW9WC/cccc.png" alt="cccc" border="0"></a></p>
<p><strong>Step 2</strong></p>
<p>Once TranslatePress 2.0.8 is downloaded. It required to be uploaded to the website using the Admin Panel’s Plugin Upload function.<br>
In the left side panel, go to Plugins and add a new plugin.</p>
<p><a href="https://ibb.co/sqWJSgM"><img src="https://i.ibb.co/fHDGRXP/ddddd.png" alt="ddddd" border="0"></a></p>
<p>Using the Add a New Plugin option Upload the Plugin that was downloaded.</p>
<p><a href="https://ibb.co/ZH7ZWWv"><img src="https://i.ibb.co/XyMwSS6/eeeee.png" alt="eeeee" border="0"></a></p>
<p>Choose the TranslatePress plugin that has to be uploaded.</p>
<p><a href="https://ibb.co/DWF2bQw"><img src="https://i.ibb.co/fFWwSHr/ffff.png" alt="ffff" border="0"></a></p>
<p>Once the plugin has been uploaded, install it.</p>
<p><a href="https://ibb.co/L5bC7dc"><img src="https://i.ibb.co/4d9jrRX/gggg.png" alt="gggg" border="0"></a></p>
<p>Then Activate the plugin.</p>
<p><a href="https://ibb.co/Cm37qxP"><img src="https://i.ibb.co/Jmw7NX3/hhhhh.png" alt="hhhhh" border="0"></a></p>
<p>Also, on the installed plugin page, the plugin can be activated.</p>
<p><a href="https://ibb.co/DfrRD0P"><img src="https://i.ibb.co/1GzmfFY/iii.png" alt="iii" border="0"></a></p>
<p><strong>Step 3</strong></p>
<p>Once the TranslatePress plugin is currently installed and activated, It will be shown on the Installed Plugins page.</p>
<p><a href="https://ibb.co/G0ZBtDQ"><img src="https://i.ibb.co/9NxzV0H/jjjj.png" alt="jjjj" border="0"></a></p>
<p>Once TranslatePress is activated, it will appear at the bottom of the settings option.</p>
<p><a href="https://ibb.co/qRw8CRh"><img src="https://i.ibb.co/tb56zbn/kkkk.png" alt="kkkk" border="0"></a></p>
<p>Navigate to the TranslatePress page in the Settings panel and choose TranslateSite.</p>
<p>The page will then redirect to a new site.<br>
Where the TranslatePress editing page is located.<br>
Using the “new string to translate” drop down menu select the Search option.</p>
<p><a href="https://ibb.co/R6JKQ0x"><img src="https://i.ibb.co/7p0DrWw/lllll.png" alt="lllll" border="0"></a></p>
<p>On the “Translate to English” field, it’s necessary to execute our code to trigger the XSS vulnerability.</p>
<p><a href="https://ibb.co/LYJmG2j"><img src="https://i.ibb.co/n6n9W5d/mmmmm.png" alt="mmmmm" border="0"></a></p>
<p>The vulnerability can be assessed by testing with a basic JavaScript alert code as shown below.</p>
<p>After Entering the script, if the field is exposed to XSS, it will display an alert stating <strong>‘This_is_XSS’</strong>.</p>
<p><a href="https://ibb.co/Px7vwfy"><img src="https://i.ibb.co/qBt3kP8/nnnn.png" alt="nnnn" border="0"></a></p>
<p>And saving the translation, an alert will be triggered every time someone visits the page.</p>
<p><a href="https://ibb.co/SJ659Kh"><img src="https://i.ibb.co/JCcmMzf/Screenshot-2024-02-21-213833.png" alt="Screenshot-2024-02-21-213833" border="0"></a></p>
<p>As shown above, once the translation was saved, an ALERT will appear on the website stating <strong>This_is_XSS</strong>.<br>
This Alert will be displayed when we visit the main webpage also.</p>
<p><a href="https://ibb.co/Y05X7GN"><img src="https://i.ibb.co/qJHCMwD/ppppp.png" alt="ppppp" border="0"></a></p>
<p>The above-mentioned approach only displays a basic alert indicating that it is vulnerable to XSS, and an attacker can use this vulnerability to get user sessions, user credentials, and senstive data exposure.</p>
<h2 id="business-impact">Business Impact</h2>
<p>A successful attack on this vulnerability may have the following consequences:</p>
<ul>
<li>Damage of Business reputation and loss of revenue</li>
<li>Unauthorized access to sensitive data, such as user passwords, personal information, and financial details, can result in data breaches.</li>
<li>Redirecting customers to phishing websites can result in financial losses and harm a company’s reputation and brand.</li>
<li>Result in decreasing customer trust.</li>
<li>Reducing the organization’s competitive advantage, resulting in missed opportunities and lower market share.</li>
</ul>
<h2 id="recommendation">Recommendation</h2>
<ul>
<li>Patch or update provided by the plugin or software vendor.</li>
<li>Implement strict input validation methods to sanitize user inputs.</li>
<li>Encode output data before displaying it on web pages to prevent dangerous scripts from running.</li>
<li>Use Content Security Policy headers to limit the sources from which content can be loaded.</li>
</ul>
<h2 id="references">References</h2>
<ul>
<li>
<p><a href="https://wpscan.com/vulnerability/b87fcc2f-c2eb-4e23-9757-d1c590f26d3f/">https://wpscan.com/vulnerability/b87fcc2f-c2eb-4e23-9757-d1c590f26d3f/</a></p>
</li>
<li>
<p><a href="https://www.exploit-db.com/exploits/50343">https://www.exploit-db.com/exploits/50343</a></p>
</li>
<li>
<p><a href="https://www.opencve.io/cve/CVE-2021-24610">https://www.opencve.io/cve/CVE-2021-24610</a></p>
</li>
</ul>

