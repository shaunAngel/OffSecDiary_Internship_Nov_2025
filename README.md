ShadowForm — Automated Web Input Vulnerability Scanner

Developer: D Shaun Angel
OffSecDiary Red Team Internship – Final Project

ShadowForm is a lightweight automated vulnerability scanner designed to detect insecure web input forms. It simulates common attack payloads such as SQL Injection and Reflected XSS to identify weak input handling mechanisms in web applications.
The tool behaves like a simplified version of Burp Suite Intruder — fully automated, fast, and non-destructive.

Legal Notice

This tool is created strictly for educational, training, and authorized security testing purposes only.
Do not scan websites without explicit permission.

Features

Automatic depth-limited web crawler

Extraction of forms, input fields, methods, and action URLs

Automated payload injection:

SQL Injection

Reflected XSS

Authentication bypass attempts

Basic IDOR pattern probing

Structured console-based vulnerability report

No headless browser required

Architecture Overview

ShadowForm is structured into six core components:

1. Web Crawler

Recursively visits internal links

Avoids duplicate URLs

Collects pages likely containing forms

2. Form Extractor

Detects HTML elements such as:
<form>, <input>, <textarea>, <select>
Captures:

HTTP method (GET/POST)

Action URL

Parameter/input names

3. Payload Engine

Maintains lists of:

SQL Injection payloads

XSS payloads

Basic authentication bypass payloads

4. Request Maker

Submits payloads via GET or POST requests

Captures full HTTP responses and status codes

5. Vulnerability Detector

Identifies:

SQL error signatures in responses

Reflected payloads indicating XSS

Authentication response anomalies

6. Reporting Engine

Outputs:

Vulnerable page URL

Affected form action

Detected vulnerability type

Payload responsible for triggering it

Installation

Ensure Python version 3.8+ is installed.

Install dependencies:

pip install requests beautifulsoup4

How to Run
python shadowform.py


When prompted, enter a target URL.
(For demonstration purposes, you may use: http://testphp.vulnweb.com)

Sample Output
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

Form action URL

Vulnerability type

Payload that triggered it

Internal Workflow

Crawling – Collect internal URLs up to a predefined depth

Form Discovery – Extract form details and input fields

Payload Injection – Submit SQLi/XSS/auth-bypass payloads

Response Analysis – Inspect HTML for error strings or reflected input

Reporting – Print vulnerabilities in a structured format

Technology Stack

Python 3

Requests (HTTP communication)

BeautifulSoup4 (HTML parsing)

urllib (URL parsing and joining)

Tested On

testphp.vulnweb.com (an intentionally vulnerable test site)

Static websites with standard HTML forms

Non–JavaScript-rendered content

Limitations

ShadowForm currently does not support:

CSRF token handling

Login-based or authenticated scanning

JavaScript-rendered forms

DOM-based XSS detection

Multi-threaded crawling

These limitations are expected in lightweight scanners and can be addressed in future updates.

Conclusion

ShadowForm automates the repetitive process of testing web input fields for common vulnerabilities.
It is suitable for Red Team reconnaissance and helps quickly highlight high-risk areas in target applications.

Planned Future Enhancements

Multi-threaded crawling

Headless browser integration

Enhanced IDOR detection

HTML/JSON report output

Advanced payload mutation & fuzzing engine

Acknowledgements

OffSecDiary Red Team Internship

VulnWeb (testphp.vulnweb.com)

Python open-source ecosystem
