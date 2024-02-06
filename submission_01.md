---


---

<h1 id="wordpress-application-vulnerable-to-ddos-attack-via-wp-cron.php">WordPress application vulnerable to DDoS attack via wp-cron.php</h1>
<p><strong>Severity : Critical</strong></p>
<h1 id="description">Description</h1>
<p>The WordPress application is vulnerable to a Distributed Denial of Service (DDoS) attack via the wp-cron.php function. Crons in WordPress are extremely significant, even if they do not pose a security risk on their own. Because wp-cron.php returns a 200 code when performed, it is feasible to launch a DDoS attack on it. WordPress uses the wp-cron.php script to automate processes like publishing scheduled articles, checking for updates, and running plugins.<br>
An attacker can exploit this vulnerability by sending a high number of responses to the wp-cron.php script, causing it to consume too many resources and overload the server. This can cause the program to become unusable or crash, potentially resulting in data loss and downtime.</p>
<h2 id="affected-target">Affected Target</h2>
<p>I found this vulnerability at <a href="http://52.66.85.112:31337/wp-cron.php">http://52.66.85.112:31337/wp-cron.php</a></p>
<h2 id="risk-rating">Risk Rating</h2>
<p>Risk: Critical<br>
Difficulty to Exploit : Low</p>
<h2 id="proof-of-concept">Proof of Concept</h2>
<p>A WordPress scan revealed a suspected DDoS attack on the site.</p>
<p><a href="https://ibb.co/DfjvwGB"><img src="https://i.ibb.co/xqrBzmn/22.png" alt="22" border="0"></a><br>
The following steps demonstrate how to launch a DoS attack on the site’s wp-cron.php file.</p>
<p><strong>Step 1</strong></p>
<p>Let us check whether the wp-cron.php is accessible. For that, let us capture the request through the Burp suite and see if it returns a 200 code.<br>
Navigate to <a href="http://52.66.85.112:31337/wp-cron.php">http://52.66.85.112:31337/wp-cron.php</a>.<br>
And capture the request with the burp.</p>
<p><a href="https://ibb.co/mJJJmJ5"><img src="https://i.ibb.co/BLLLmL2/1.png" alt="1" border="0"></a></p>
<p>Send it to the Burp repeater.</p>
<p><a href="https://ibb.co/ZNkzJDB"><img src="https://i.ibb.co/8XSgBZr/Screenshot-2024-02-06-235908.png" alt="Screenshot-2024-02-06-235908" border="0"></a></p>
<p>And check  the code through the response tab</p>
<p><a href="https://ibb.co/nCbLgD0"><img src="https://i.ibb.co/PQN6m5Y/Screenshot-2024-02-06-235925.png" alt="Screenshot-2024-02-06-235925" border="0"></a></p>
<p>As we can see below, when we go to the <a href="http://52.66.85.112:31337/wp-cron.php">http://52.66.85.112:31337/wp-cron.php</a> site, it shows a 200 (Success) code response instead of a 403 (Forbidden) code.</p>
<p><strong>Step 2</strong></p>
<p>We can validate that the wp-cron.php file is accessible and may be vulnerable to a denial of service attack.<br>
Let’s try to exploit it.</p>
<p>Get the  Python file that is required to launch the DoS attack. (<a href="http://doser.py">doser.py</a>) script at  <a href="https://github.com/Quitten/doser.py">https://github.com/Quitten/doser.py</a><br>
<a href="https://imgbb.com/"><img src="https://i.ibb.co/m9DW9ww/12121.png" alt="12121" border="0"></a></p>
<p><strong>Step 3</strong></p>
<p>Once the <a href="http://doser.py">doser.py</a> script has been set up, execute the following command to run the script file on the target vulnerable URL.</p>
<p><a href="https://ibb.co/JFQFmGy"><img src="https://i.ibb.co/pryrbMR/1212121212.png" alt="1212121212" border="0"></a></p>
<p>The command instructs the script to execute a DoS (Denial of Service) attack by creating 999 concurrent threads (-t), each of which sends HTTP GET requests (-g) to a target server.</p>
<p><strong>Step 4</strong></p>
<p>After around 1000+ requests, check visiting the website.</p>
<p><a href="https://ibb.co/Cb6TDY4"><img src="https://i.ibb.co/VgxP5zb/Screenshot-19.png" alt="Screenshot-19" border="0"></a></p>
<p>As we can see above, after 1200+ requests, the website went down.</p>
<h2 id="business-impact">Business Impact</h2>
<p>A successful attack on this vulnerability may have the following consequences:</p>
<ul>
<li>Potential data loss and downtime.</li>
<li>Damage of Business reputation and loss of revenue</li>
<li>Mitigating the effects of a DoS attack on wp-cron.php could require significant costs, including time, effort, and financial expenses. This may include deploying new infrastructure, establishing security measures, and doing investigations to determine the source of the attack.</li>
<li>Denial of Service (DoS) attacks can make an application unavailable,</li>
<li>Server overload and increased resource usage, leading to slow response times or application crashes.</li>
</ul>
<h2 id="recommendation">Recommendation</h2>
<ul>
<li>To mitigate this vulnerability, disable WordPress’s default<br>
wp-cron.php script and instead set up a server-side cron job.</li>
<li>Access the wp-cron.php file from the root directory and edit the<br>
file. Include the below code line to it and save it.<br>
define(‘DISABLE_WP_CRON’, true);</li>
<li>Configure rate limiting methods to limit the number of queries<br>
delivered to wp-cron.php.</li>
<li>Implement a WAF to monitor the incoming HTTP traffic and filter out malicious requests before they reach the server.</li>
</ul>
<h2 id="references">References</h2>
<ul>
<li>
<p><a href="https://www.iplocation.net/defend-wordpress-from-ddos">https://www.iplocation.net/defend-wordpress-from-ddos</a></p>
</li>
<li>
<p><a href="https://medium.com/@thecpanelguy/the-nightmare-that-is-wpcron-php-ae31c1d3ae30">https://medium.com/@thecpanelguy/the-nightmare-that-is-wpcron-php-ae31c1d3ae30</a></p>
</li>
</ul>

