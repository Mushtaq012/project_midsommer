---


---

<h1 id="xmlrpc.php-file-is-enable-it-can--be-used-for-ddos-and-bruteforce-attack">xmlrpc.php file is enable it can  be used for (DDOS) and bruteforce attack</h1>
<p><strong>Severity : High</strong></p>
<h1 id="description">Description</h1>
<p>WordPress’s XML-RPC is an API (application program interface) that allows external applications, such mobile apps or desktop software, to communicate with a WordPress website.<br>
The main flaws of XML-RPC are brute force attacks, XSPA (Cross Site Port Scanning) attacks, and DDoS attacks. Attackers try to access or gather information about WordPress using the flaws in the xmlrpc.php.</p>
<h2 id="affected-target">Affected Target</h2>
<p>I found this vulnerability at <a href="http://15.206.81.14:31337/xmlrpc.php">http://15.206.81.14:31337/xmlrpc.php</a></p>
<h2 id="risk-rating">Risk Rating</h2>
<p>Risk: High<br>
Difficulty to Exploit : Medium</p>
<h2 id="proof-of-concept">Proof of Concept</h2>
<p>A WordPress scan revealed that the xmlrpc.php file is enabled on the site.</p>
<p><a href="https://imgbb.com/"><img src="https://i.ibb.co/hdfpvZy/xsx.png" alt="xsx" border="0"></a></p>
<p>The following steps demonstrate how to perform a pingback.ping and Brute-force attack on the xmlrpc.php file.</p>
<p><strong>Step 1</strong><br>
The first step is to send a POST request to the server, which returns a list of all possible methods. This method is critical because it provides insight into the operations that can be performed using the XML-RPC interface. A comprehensive list of methods can help identify potential attack vectors and target specific actions for exploitation.</p>
<p>Let us check whether the xmlrpc.php is accessible. For that, let us capture the request through the Burp suite and observe the request.</p>
<p>Navigate to <a href="http://15.206.81.14:31337/xmlrpc.php">http://15.206.81.14:31337/xmlrpc.php</a>.<br>
And capture the request with the burp.</p>
<p><a href="https://ibb.co/yppMcLQ"><img src="https://i.ibb.co/VxxhcXq/asas.png" alt="asas" border="0"></a></p>
<p>Send it to the Burp repeater.</p>
<p><a href="https://ibb.co/hCRDyT3"><img src="https://i.ibb.co/fQY42Tj/1111.png" alt="1111" border="0"></a></p>
<p>Check the response via the response tab; here, we can see that a response was shown as “XML-RPC server accepts POST requests only.”</p>
<p><a href="https://ibb.co/RgMXXgj"><img src="https://i.ibb.co/Gd1ZZdH/A1.png" alt="A1" border="0"></a></p>
<p>Let’s try changing the request method to POST and check the response.<br>
<a href="https://ibb.co/KstR0f6"><img src="https://i.ibb.co/M1zW2tn/A2.png" alt="A2" border="0"></a></p>
<p>We can see once we change the request method we can get a 200 code on the response.</p>
<p><a href="https://ibb.co/T2GBLLr"><img src="https://i.ibb.co/mTKC88S/Screenshot-2024-02-16-142111231231202.png" alt="Screenshot-2024-02-16-142111231231202" border="0"></a></p>
<p><strong>Step 2</strong></p>
<p>To list all methods. Send a POST request with the following POST data, as shown in the figure, and you will receive a response with all the methods available.<br>
<a href="https://imgbb.com/"><img src="https://i.ibb.co/PG43Jxm/asasas.png" alt="asasas" border="0"></a></p>
<p><a href="https://ibb.co/Brkr7jB"><img src="https://i.ibb.co/X3H3dpt/a12.png" alt="a12" border="0"></a><br>
Check that the following options are available before proceeding with the brute-forcce attack:</p>
<ul>
<li>wp.getUserBlogs</li>
<li>wp.getCategories</li>
</ul>
<p>Here are some common methods used for brute-force . There are many other methods also available.</p>
<p>For XSPA attack we need to check the method <em>pingback.ping</em><br>
Is available or not.</p>
<p><strong>Step 3 Brute-Force</strong></p>
<p>To do a brute-force, use the following request on a POST method. with some valid usernames and passwords</p>
<p><a href="https://ibb.co/PwmLq6B"><img src="https://i.ibb.co/Gcx6z5g/asasx.png" alt="asasx" border="0"></a><br>
<a href="https://ibb.co/HGZ78bm"><img src="https://i.ibb.co/F8p6TyG/bf.png" alt="bf" border="0"></a><br>
Whether we enter the incorrect credentials or the correct credentials, the response will get a 200 OK code, therefore we should decide which is correct and which is wrong based on the size and the contents on the response.<br>
Using the XML-RPC API, attackers can make numerous login attempts without triggering rate-limiting or detection measures.</p>
<p><a href="https://ibb.co/Tbxs9kQ"><img src="https://i.ibb.co/0FRxHc0/acxz.png" alt="acxz" border="0"></a></p>
<p>If the xmlrpc.php file is correctly configured, it will not allow multiple attempts where it checks the X number of credentials and returns the same results for other responses. As shown above, even if we enter the correct credentials at the end, it only checks the credentials we entered first, but we can check them one by one without being identified by the server. We can also perform a brute force as usual, forwarding this request to an intruder.</p>
<p><a href="https://ibb.co/wNtQpgM"><img src="https://i.ibb.co/6RQtDwg/bfa.png" alt="bfa" border="0"></a><br>
<a href="https://ibb.co/FHkrFHY"><img src="https://i.ibb.co/XYfQqY5/bfa3.png" alt="bfa3" border="0"></a></p>
<p><strong>Step 3 Pingback.ping attacks</strong></p>
<p>Let us use the pingback.ping technique to launch an XSPA attack.<br>
In this attack, the user types in a URL and sends it to the program, but the application fails to validate or sanitize the back-end response from remote servers before giving it to the client. This attack is carried out to obtain information about IP addresses and TCP ports.</p>
<p>The susceptible website receives a request with the URL provided by the burp collaborator as a callback.</p>
<p>Copy the collaborator link.</p>
<p><a href="https://ibb.co/4Wd0vgN"><img src="https://i.ibb.co/hsfTQ18/acc.png" alt="acc" border="0"></a></p>
<p>Paste it with the server and port, then for the valid bug site string, insert the URL of a blog on the site where we will search for vulnerabilities.</p>
<p><a href="https://ibb.co/Y3LW5St"><img src="https://i.ibb.co/rmwtBhZ/cdcd.png" alt="cdcd" border="0"></a></p>
<p>Once the request is ready, send it and see the response. If the response has a string greater than zero, it indicates that the port is open. To check the port, navigate to the collabarator tab and monitor the responses received by the server from whatever port.</p>
<p><a href="https://ibb.co/26RkwLB"><img src="https://i.ibb.co/BPvCm7R/asasdasd.png" alt="asasdasd" border="0"></a></p>
<p>Here we can see that our server has received two DNS and two HTTP responses from a certain IP address and port, however the port from which the responses were received is not open.</p>
<p>Also the pingback.ping is also can be used to perform a DDoS attack</p>
<p><a href="https://ibb.co/yYCdYQh"><img src="https://i.ibb.co/X3Pj3Cy/xxxs.png" alt="xxxs" border="0"></a></p>
<p>In the above command I have entered a webhook url to receive the pingback requests from the vulnerable website. When it triggers the server, I will obtain a log file from the victim on my server,</p>
<p><a href="https://ibb.co/rv5qMSg"><img src="https://i.ibb.co/M9PKp4b/web.png" alt="web" border="0"></a></p>
<p>and once I submit several requests automatically, I will be able to launch a DDoS attack against it.</p>
<h2 id="business-impact">Business Impact</h2>
<p>A successful attack on this vulnerability may have the following consequences:</p>
<ul>
<li>Damage of Business reputation and loss of revenue</li>
<li>Potential data loss and downtime.</li>
<li>Distributed Denial of Service (DDoS) attacks can make an application unavailable,</li>
<li>The WordPress website was compromised, allowing attackers to obtain illegal access to the site’s backend.</li>
<li>Attackers can utilize XML-RPC vulnerabilities to send spam or comments from the compromised WordPress site.</li>
</ul>
<h2 id="recommendation">Recommendation</h2>
<ul>
<li>Blocking XMLRPC on Cloudflare to prevent it from ever reaching your server.</li>
<li>To address this vulnerability, disable XMLRPC on the server and use security plugins like Wordfence, Sucuri, or iThemes Security in WordPress.</li>
<li>Use strict file permissions or server-side access controls like IP whitelisting and blacklisting.</li>
<li>Keep an eye out for any strange activity on your WordPress site, such as failed login attempts.</li>
</ul>
<h2 id="references">References</h2>
<ul>
<li>
<p><a href="http://xmlrpc.com/">http://xmlrpc.com/</a></p>
</li>
<li>
<p><a href="https://kinsta.com/blog/xmlrpc-php/">https://kinsta.com/blog/xmlrpc-php/</a></p>
</li>
</ul>

