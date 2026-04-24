# Repeater

## What is Repeater?
- Repeater is a tool in Burp Suite for manually replaying HTTP requests
- Allows sending same request multiple times with modifications
- See server response immediately after each send
- Most used tool for manual vulnerability testing
- Essential for testing SQL injection XSS and other vulnerabilities

---

## How to Send Request to Repeater
Method 1 → Right click request in Proxy history → Send to Repeater
Method 2 → Ctrl + R keyboard shortcut
Method 3 → Right click in Intercept tab → Send to Repeater

---

## Repeater Layout
Left panel → Request editor
Right panel → Response viewer
Top → Send button and tab navigation
Bottom → Status bar with response time and length

---

## Sending Requests

Send request to Repeater from Proxy
Modify any part of request
Click Send button
Response appears in right panel
Modify again and resend
Repeat as many times as needed

---

## Response View Options
Pretty → formatted readable response
Raw → raw response text
Hex → hexadecimal view
Render → rendered HTML page

---

## Common Uses of Repeater

### Testing SQL Injection
Original request:
GET /product?id=1 HTTP/1.1
Test payloads one by one:
GET /product?id=1' HTTP/1.1
GET /product?id=1 OR 1=1-- HTTP/1.1
GET /product?id=1 AND 1=2-- HTTP/1.1

### Testing XSS
Original:
GET /search?q=hello HTTP/1.1
Test payloads:
GET /search?q=<script>alert(1)</script> HTTP/1.1
GET /search?q=<img src=x onerror=alert(1)> HTTP/1.1

### Testing IDOR
Original:
GET /profile?id=100 HTTP/1.1
Modified:
GET /profile?id=101 HTTP/1.1
GET /profile?id=102 HTTP/1.1

### Testing Authentication Bypass
Original:
Cookie: role=user
Modified:
Cookie: role=admin
Cookie: isAdmin=true

## Important Points
- Repeater is best tool for manual testing
- Always start with original request then modify
- Check response length and status code for changes
- Render tab shows actual page rendered in browser
- Multiple repeater tabs help organize testing

