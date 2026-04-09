# What is Burp Suite?

## Introduction
- Burp Suite is the most popular web application security testing tool
- Developed by PortSwigger company
- Used by security professionals and ethical hackers worldwide
- Acts as a proxy between browser and web application
- Intercepts modifies and replays HTTP and HTTPS requests
- Used for finding vulnerabilities in web applications
- Comes pre-installed on Kali Linux
- Industry standard tool for web penetration testing

---

## Burp Suite Editions

### Burp Suite Community Edition
- Free version available to everyone
- Basic features included
- Manual testing capabilities
- Limited scanner functionality
- Good for learning and basic testing
- Available on Kali Linux by default

### Burp Suite Professional Edition
- Paid version costs around 449 USD per year
- Full automated scanner
- Advanced intruder attack types
- Burp Collaborator for out of band testing
- Save and restore project files
- Most professionals use this edition

### Burp Suite Enterprise Edition
- For large organizations
- Automated scanning at scale
- CI CD pipeline integration
- Multiple concurrent scans
- Centralized management dashboard

---

## What Can Burp Suite Do?
- Intercept and modify HTTP HTTPS requests
- Replay modified requests to server
- Brute force login forms and parameters
- Scan for common web vulnerabilities
- Find SQL injection vulnerabilities
- Find XSS vulnerabilities
- Find CSRF vulnerabilities
- Find authentication bypasses
- Find insecure direct object references
- Find file inclusion vulnerabilities
- Decode and encode data in multiple formats
- Compare two responses or requests
- Map web application structure
- Spider entire web application

---

## Burp Suite Main Tools

### Proxy
- Intercepts HTTP HTTPS traffic
- Sits between browser and web server
- Allows viewing and modifying requests
- Core feature of Burp Suite
- All traffic passes through proxy

### Repeater
- Manually send and replay requests
- Modify parameters and headers
- See response immediately
- Test same request with different inputs
- Essential for manual vulnerability testing

### Intruder
- Automated attack tool
- Brute force parameters and fields
- Fuzz inputs with payloads
- Find injection points
- Test many inputs automatically

### Scanner
- Automated vulnerability scanner
- Finds common web vulnerabilities
- Active and passive scanning modes
- Professional edition has full scanner
- Community edition has limited scanning

### Decoder
- Encode and decode data
- Supports Base64 URL HTML hex
- Convert between formats
- Useful for analyzing encoded parameters

### Comparer
- Compare two requests or responses
- Find differences between them
- Useful for analyzing authentication
- Spot subtle differences in responses

### Spider
- Crawls entire web application
- Discovers all pages and links
- Maps application structure
- Finds hidden content

### Sequencer
- Analyzes randomness of tokens
- Tests session token strength
- Finds predictable tokens
- Important for session security testing

### Extender
- Add plugins to Burp Suite
- BApp Store has many extensions
- Custom extensions in Java Python Ruby
- Extends functionality greatly

---

## How Burp Suite Works

### Proxy Architecture
Browser → Burp Suite Proxy → Web Server
↑
Attacker intercepts
modifies requests here

### Request Flow
- Browser sends HTTP request
- Request goes to Burp proxy first
- Burp captures and displays request
- Tester can modify request
- Modified request sent to server
- Server response captured by Burp
- Response displayed and can be modified
- Modified response sent to browser

---

## Common Web Vulnerabilities Found with Burp Suite

### Injection Vulnerabilities
- SQL Injection → malicious SQL in parameters
- Command Injection → OS commands in inputs
- LDAP Injection → LDAP queries manipulation
- XML Injection → XML data manipulation

### Authentication Issues
- Brute force login → try many passwords
- Username enumeration → find valid usernames
- Weak session tokens → predictable tokens
- Password in URL → credentials exposed

### Access Control Issues
- IDOR → access other users data by changing ID
- Privilege escalation → access admin functions
- Missing function level access control

### Injection via Client
- XSS → inject JavaScript into pages
- CSRF → force user to make requests
- Clickjacking → trick user clicks

### Other Vulnerabilities
- Directory traversal → access files outside webroot
- File inclusion → include arbitrary files
- XML external entities XXE
- Server side request forgery SSRF
- Insecure deserialization


---

## Important Points
- Burp Suite is the industry standard for web application testing
- Community edition is enough for learning
- Always use Burp Suite only on authorized applications
- PortSwigger Web Security Academy is best free resource
- Practice on intentionally vulnerable applications first
- Burp Suite works with all modern browsers
- HTTPS requires certificate installation in browser
- All major bug bounty hunters use Burp Suite
- Learning Burp Suite is essential for web security career
