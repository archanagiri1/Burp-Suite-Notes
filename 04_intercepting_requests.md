# Intercepting Requests

## What is Request Interception?
- Intercepting means stopping request before it reaches server
- Burp Proxy captures every request from browser
- Tester can view and modify request before sending
- Can also intercept and modify server responses
- Core technique in web application testing
- Allows manual manipulation of all parameters

---

## How Interception Works
Browser sends request
↓
Burp Proxy catches request
↓
Request shown in Intercept tab
↓
Tester views and modifies request
↓
Forward sends modified request to server
↓
Server sends response
↓
Burp catches response optionally
↓
Response forwarded to browser

---

## Turning Intercept On and Off
Proxy tab → Intercept subtab
Click button to toggle:
Intercept is ON → stops every request
Intercept is OFF → traffic flows freely

---

## Intercepting HTTP Requests

### Step by Step
Open Burp Suite
Configure browser proxy to 127.0.0.1:8080
Go to Proxy → Intercept tab
Make sure Intercept is ON
Go to any website in browser
Request appears in Intercept tab
View and modify request
Click Forward to send to server
Or click Drop to discard request


---

---

## Request Structure in Intercept

### Request Line
GET /login HTTP/1.1
POST /submit HTTP/1.1
PUT /update HTTP/1.1

### Body Section
username=admin&password=test
{"user":"admin","pass":"test"}

---

## Modifying Requests

### Modify Parameters
Original:
username=admin&password=test

Modified:
username=admin&password=admin123
username=administrator&password=test
username=admin'--&password=anything

### Modify Headers
Original:
User-Agent: Mozilla/5.0 Windows
Modified:
User-Agent: sqlmap/1.0
X-Forwarded-For: 127.0.0.1
X-Admin: true

### Modify Request Method
Original:
GET /profile?id=1 HTTP/1.1
Modified:
POST /profile HTTP/1.1
Content-Type: application/x-www-form-urlencoded
id=1

---

## Intercepting HTTPS Traffic
Requirement: Burp CA certificate installed in browser
Without certificate: SSL error appears
With certificate: HTTPS traffic fully visible
All HTTPS requests intercepted same as HTTP

---

## Intercepting Responses

### Enable Response Interception
Proxy → Options → Intercept Server Responses
Check: Intercept responses based on rules
Check: Intercept in scope items only
Click Add rule

### Why Intercept Responses?
- Modify response content before browser renders
- Remove security headers to test impact
- Change response codes to test behavior
- Modify JavaScript before execution
- Enable hidden features in responses

---

## HTTP History

### What is HTTP History?
- Keeps record of all requests through proxy
- Even when intercept is OFF
- Can go back and review any past request
- Can send any past request to other tools

### Using HTTP History
Proxy → HTTP history tab
All requests listed with details
Click any request to view details
Bottom panel shows request and response
Right click for options

### HTTP History Columns
→ request number
Host → target hostname
Method → GET POST etc
URL → request path
Params → has parameters
Edited → was request modified
Status → HTTP response code
Length → response size
MIME type → response type
Extension → file extension
Title → page title
Comment → your notes
Time → when request made

### Filtering HTTP History
Click Filter bar at top of history
Filter by:

Search term in URL
Show only in scope items
Show only parameterized requests
Filter by status code
Filter by MIME type
Filter by file extension
Filter by annotation


---

## Sending Requests to Other Tools

### Send to Repeater
Right click request → Send to Repeater
Ctrl + R keyboard shortcut
Test same request with many modifications
Best for manual vulnerability testing

### Send to Intruder
Right click request → Send to Intruder
Ctrl + I keyboard shortcut
Automate testing with payloads
Best for brute force and fuzzing

### Send to Decoder
Right click request → Send to Decoder
Analyze encoded parameters
Decode Base64 URL encoded values

### Send to Comparer
Right click request → Send to Comparer
Compare two different requests
Compare two different responses
Find subtle differences

---

## Practical Interception Examples

### Example 1 - Modifying Login Request

Go to login page
Turn intercept ON
Enter any credentials and submit
Request appears in Burp:
POST /login HTTP/1.1
Host: target.com
username=user&password=test
Modify password field
Click Forward
Observe response


### Example 2 - Changing User ID

Login to application
Go to profile page
Intercept request:
GET /profile?id=123 HTTP/1.1
Change id parameter:
GET /profile?id=124 HTTP/1.1
Forward request
Check if another users profile shows
This tests for IDOR vulnerability


### Example 3 - Adding Admin Header

Intercept any request
Add header to request:
X-Admin: true
X-Role: administrator
X-Forwarded-For: 127.0.0.1
Forward request
Check if admin access granted


### Example 4 - Modifying Cookie

Login as normal user
Intercept request
Find cookie in request:
Cookie: role=user
Modify cookie:
Cookie: role=admin
Forward request
Check if admin access granted


---

## Important Points
- Turn intercept OFF when not actively testing
- HTTP history captures all traffic even with intercept OFF
- HTTPS requires CA certificate installed in browser
- Always send interesting requests to Repeater for testing
- Modifying cookies can reveal access control issues
- Match and replace automates repetitive modifications
- Scope configuration reduces unwanted traffic
- Forward modified requests to test application behavior
- Drop requests to block specific traffic
- Always test only on authorized applications
