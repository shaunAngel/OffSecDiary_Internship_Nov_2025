ShadowForm — Automated Web Input Vulnerability Scanner
Developer: D Shaun Angel | OffSecDiary Red Team Internship Final Project

ShadowForm is a lightweight automated vulnerability scanner designed to detect insecure web input forms. It simulates common attack payloads such as SQL Injection and Reflected XSS to identify weak input handling mechanisms in web applications.
It behaves like a simplified version of Burp Suite Intruder — fully automated and non-destructive.

⚠️Legal Notice (Important)
This tool is created strictly for educational and authorized security testing only.
Do NOT scan websites without explicit permission.

♦︎Features
Automatic web crawler (depth-limited)
Form extraction (inputs, method, action)
-Automated payload injection:
SQL Injection
Reflected XSS
Authentication bypass
Basic IDOR pattern detection
Structured vulnerability report
Works without any headless browser

♦︎Architecture Overview

ShadowForm consists of six major components:

1. Web Crawler
Recursively visits internal links
Avoids duplicates
Collects pages containing forms

2. Form Extractor
Detects:
<form>, <input>, <textarea>, <select>
Captures:
Method (GET/POST)
Action URL
Input field names

3. Payload Engine
SQLi payload list
XSS payload list
Basic auth-bypass payloads

4. Request Maker
Submits payloads via GET/POST
Captures HTML responses & status codes

5. Vulnerability Detector
Detects:
SQL errors
Reflected XSS
Authentication anomalies

6. Reporting Engine
Outputs:
Vulnerable pages
Payload that triggered the vulnerability
Vulnerability category

♦︎How to Install
Make sure Python 3.8+ is installed.
Install dependencies:
pip install requests beautifulsoup4

▶️ How to Run
python shadowform.py
(When prompted, enter the target URL:http://testphp.vulnweb.com)

♣︎Sample Output
------ SHADOWFORM REPORT ------

Page: http://testphp.vulnweb.com
Form Action: http://testphp.vulnweb.com/search.php?test=query
Vulnerability: SQL Injection
Payload: admin'--

Page: http://testphp.vulnweb.com/categories.php
Vulnerability: Reflected XSS
Payload: <script>alert(1)</script>


Each finding includes:

Page URL
Form action
Vulnerability type
Working payload

 How It Works (Internal Logic)

1️⃣ Crawling — Collects internal URLs
2️⃣ Form Discovery — Extracts all forms and inputs
3️⃣ Payload Injection — Fills fields with SQLi/XSS payloads
4️⃣ Response Analysis — Checks for errors or reflected payloads
5️⃣ Reporting — Prints vulnerabilities in the console

♦︎Technology Stack

Python 3
Requests (HTTP communication)
BeautifulSoup4 (HTML parsing)
urllib (URL joining & routing)

♦︎Tested On

testphp.vulnweb.com (intentionally vulnerable site)
Standard HTML-based forms
Static websites without JavaScript rendering

 ♦︎Limitations
ShadowForm currently does NOT handle:
CSRF tokens
Authentication workflows
JavaScript-rendered forms
DOM-based XSS
Multi-threaded crawling
These can be added in future enhancements.

🏁 Conclusion

ShadowForm automates the repetitive and time-consuming task of testing form inputs for vulnerabilities.
It is ideal for Red Teamers during reconnaissance and helps quickly identify high-risk insecure input fields.

📌 Future Improvements

Multithreaded crawling

Headless browser support

Improved IDOR detection

HTML/JSON report generation

Advanced payload mutation (fuzzing engine)

🙌 Acknowledgements

OffSecDiary Red Team Internship

Vulnerable test site: testphp.vulnweb.com

Python open-source libraries
