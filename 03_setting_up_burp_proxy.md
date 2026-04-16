# Setting Up Burp Proxy

## What is Burp Proxy?
- Burp Proxy sits between browser and web server
- Intercepts all HTTP and HTTPS traffic
- Allows viewing and modifying every request
- Default runs on 127.0.0.1 port 8080
- Must configure browser to use Burp as proxy
- Must install Burp certificate for HTTPS

---

## Step 1 - Start Burp Suite
```bash
# start burp suite
burpsuite

# select temporary project
# click next
# use burp defaults
# click start burp
```

---

## Step 2 - Check Proxy Listener
Proxy tab → Options subtab
Check listener is running on 127.0.0.1:8080
Green circle means listener is active


---

## Step 3 - Configure Firefox Browser

### Manual Method
Firefox → Settings
Search: proxy
Click Network Settings
Select Manual proxy configuration
HTTP Proxy: 127.0.0.1
Port: 8080
Check: Also use this proxy for HTTPS
Click OK

### Using FoxyProxy Extension
Install FoxyProxy extension in Firefox
Click FoxyProxy icon in toolbar
Click Add New Proxy
Title: Burp Suite
Proxy Type: HTTP
Proxy IP: 127.0.0.1
Port: 8080
Save
Enable FoxyProxy
Select Burp Suite profile

---

## Step 4 - Install Burp Certificate for HTTPS

### Why Certificate Needed?
- Without certificate HTTPS sites show error
- Burp cannot intercept HTTPS without certificate
- Certificate tells browser to trust Burp

### Install Certificate Steps
Make sure Burp proxy is running
Open Firefox
Go to http://burp
Click CA Certificate button
File cacert.der downloads automatically
Firefox → Settings → Privacy and Security
Scroll down to Certificates section
Click View Certificates
Click Authorities tab
Click Import button
Select downloaded cacert.der file
Check Trust this CA to identify websites
Click OK
Restart Firefox

---

## Step 5 - Test Proxy is Working
Make sure Burp intercept is ON
Open Firefox
Go to any website like http://example.com
Request should appear in Burp Proxy Intercept tab
Click Forward to send request
Website loads in browser

---

## Step 6 - Turn Intercept On and Off
Proxy tab → Intercept subtab
Intercept is ON → currently intercepting all requests
Intercept is OFF → traffic passes through without stopping
Toggle button to switch between modes

---

## Proxy Listener Configuration

### Default Listener
127.0.0.1:8080
Only accepts connections from local machine

### Add New Listener
Proxy → Options → Proxy Listeners
Click Add button
Enter binding port
Enter binding address
Click OK

### Change Default Port
Proxy → Options → Proxy Listeners
Select existing listener
Click Edit
Change port number
Click OK

---

## Intercept Rules Configuration

### Request Interception Rules
Proxy → Options → Intercept Client Requests
Rules control which requests are intercepted
Default intercepts all requests
Can filter by URL file type method

### Response Interception Rules
Proxy → Options → Intercept Server Responses
By default responses not intercepted
Enable to intercept and modify responses

---

## Match and Replace Rules
Proxy → Options → Match and Replace
Automatically modify requests and responses
Examples:

Replace User-Agent header
Add custom header to all requests
Replace specific parameter value
Remove unwanted headers


---

## SSL Pass Through
Proxy → Options → SSL Pass Through
Add hosts to bypass SSL interception
Useful for apps that use certificate pinning
Add host and Burp will not intercept SSL

---

## Proxy History
Proxy → HTTP history
Shows all requests made through proxy
Filter by:

Host
Method
URL
Status code
Response length
MIME type
Right click any request for options


---

## Common Proxy Problems and Fixes

### Browser Shows Proxy Error
Problem: Browser cannot connect to proxy
Fix: Check Burp Suite is running
Fix: Check proxy listener is on 127.0.0.1:8080
Fix: Check browser proxy settings match

### HTTPS Sites Show Certificate Error
Problem: SSL certificate error on HTTPS sites
Fix: Install Burp CA certificate in browser
Fix: Follow certificate installation steps above

### Requests Not Appearing in Burp
Problem: Traffic not showing in Burp
Fix: Check intercept is turned ON
Fix: Check browser proxy settings
Fix: Check Burp listener is active
Fix: Disable browser extensions that bypass proxy

### Burp Port Already in Use
Problem: Port 8080 already in use
Fix: Change Burp listener port to 8081 or 9090
Fix: Update browser proxy settings to match new port

---

## FoxyProxy Setup for Easy Switching
Advantage of FoxyProxy:

Quickly switch proxy on and off
Switch between multiple proxy profiles
No need to go into browser settings each time

Setup:

Install FoxyProxy Standard extension
Create Burp profile on 127.0.0.1:8080
Click icon to enable or disable quickly


---

## Important Points
- Always start Burp before opening browser
- Install CA certificate once per browser
- Use FoxyProxy for quick proxy switching
- Turn intercept OFF when just browsing
- Turn intercept ON when testing specific requests
- Proxy history keeps record of all traffic
- Scope configuration reduces unnecessary traffic
- HTTPS requires certificate installation
- Default port 8080 can be changed if needed
- Always disable proxy in browser after testing
