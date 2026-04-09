# Burp Suite Interface

## Starting Burp Suite
```bash
# start from terminal
burpsuite

# or applications menu
# Applications → Web Application Analysis → burpsuite
```
---

## Proxy Tab
- Most important tab in Burp Suite
- Intercept subtab → view and modify requests
- HTTP history subtab → all past requests
- WebSockets history → WebSocket traffic
- Options subtab → proxy configuration
- Default listener → 127.0.0.1:8080

---
## Target Tab
- Shows site map of target application
- All discovered content shown here
- Scope configuration done here
- Right click host to add to scope
- Filter content by various criteria

---
## Repeater Tab
- Send and replay modified requests
- Left panel → request editor
- Right panel → response viewer
- Send button → sends request to server
- History navigation with arrows
- Response views → Pretty Raw Hex Render

---
## Intruder Tab
- Automated attack tool
- Four attack types:
  - Sniper → one payload one position
  - Battering Ram → same payload all positions
  - Pitchfork → different payloads each position
  - Cluster Bomb → all combinations
- Positions subtab → mark payload positions with §
- Payloads subtab → configure wordlists

---
## Decoder Tab
- Encode and decode data
- Supported formats:
  - URL
  - HTML
  - Base64
  - ASCII Hex
  - Hex
  - Octal
  - Binary
  - Gzip
  - Hash MD5 SHA1 SHA256

---
## Comparer Tab
- Compare two requests or responses
- Word level comparison
- Byte level comparison
- Color coding:
  - Orange → modified
  - Red → deleted
  - Green → added

---
## Right Click Options in Proxy History
- Send to Repeater
- Send to Intruder
- Send to Decoder
- Send to Comparer
- Copy URL
- Add to scope
- Add comment

---

## Important Points
- Always set scope before testing
- Learn Proxy and Repeater first
- Community edition Intruder is speed limited
- Install extensions from BApp Store
- HTTP history keeps all past requests
- Right click is fastest way to send to other tools

