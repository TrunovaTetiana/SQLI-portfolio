
# 🧪 SQL Injection — High Security Level (DVWA)

## 👤 Tester:
**Name:** Tetiana Trunova  
**Environment:** Kali Linux (Parallels), Burp Suite, Google Chrome  
**Objective:** Test for the presence of SQL Injection vulnerability when DVWA security is set to "High".

## 📍 Target Page:
- Application: DVWA (Damn Vulnerable Web Application)  
- Section: `SQL Injection`  
- Security Level: `High`  
- URL:  
  ```
  http://192.168.1.48/dvwa/vulnerabilities/sqli/
  ```

## 🔧 Preparation:
1. Launched Kali Linux with Burp Suite  
2. Connected Google Chrome to Burp via Proxy  
3. Opened DVWA and selected the `SQL Injection` vulnerability  
4. Set security level to `High` in DVWA Security settings  
5. Intercepted request with `id=1` via **Burp Proxy**  
6. Sent the request to **Repeater** for payload testing

## 🔍 Test 1: Classic SQL Injection
**Payload:**  
```
?id=1 OR 1="1"
```
**Result:**  
- Application returns standard page output  
- No error or unexpected data displayed  
**Conclusion:** Classic SQL injection is blocked by prepared statements.

## 🧪 Test 2: Passing an Array Instead of Integer
**Payload:**  
```
?id[]=1
```
**Method:**  
- Modified the `id=1` parameter to `id[]=1` in Burp Repeater  
**Result:**  
- Server returned a blank HTML response with HTTP 200 OK  
- No error was triggered  
**Conclusion:** The server ignored the array input without returning an error. This indicates suppressed error reporting or weak type validation. This could lead to a logical vulnerability in a real-world application.

## 🧠 Test 3: Attempting SQL Injection via `UNION SELECT`
**Payload:**  
```
?id=1 UNION SELECT NULL, version() -- 
```
**Method:**  
- Manually entered payload in browser address bar  
- Used `view-source:` and Chrome DevTools to analyze HTML/DOM  
**Observation:**  
- Page output remained unchanged:
  ```html
  <p>Hello admin</p>
  <p>Your Login ID is 1</p>
  ```
- No SQL data or `version()` output appeared  
**Conclusion:** The injection was neutralized. The system likely uses `bindParam` with strict typing, effectively blocking injected SQL code.

## 🔍 General Analysis:
- DVWA’s High level uses **prepared statements with `bindParam()`**  
- Inputs are sanitized and passed as **typed parameters (e.g., `PDO::PARAM_INT`)**  
- All attempts using `OR`, `UNION`, `SLEEP`, arrays, and headers failed — this confirms **solid SQL injection defense**

## ✅ Recommendations (for developers):
- Continue using **prepared statements**  
- Enforce strict **type checking** on user input  
- Log suspicious or malformed inputs (e.g., arrays or strings in numeric fields)  
- Enable detailed error reporting in development environments for detection

## 📁 Report Category:
`[SQL Injection / Secure Input / High Level / Defense Confirmed]`

## 🖼️ Screenshots:

> Below are actual screenshots captured during testing. All images are located in the `screenshot/` subfolder.

1. ![sqli-h-1.png](/sqli-h-1.png)  
   _DVWA interface with SQL Injection (High) selected_

2. ![sqli-h-2.png](/sqli-h-2.png)  
   _Intercepted HTTP request using Burp Proxy_

3. ![sqli-h-3.png](/sqli-h-3.png)  
   _Repeater: payload with array injection `id[]=1`_

4. ![sqli-h-4.png](/sqli-h-4.png)  
   _Response from server: blank page (no result)_

5. ![sqli-h-5.png](/sqli-h-5.png)  
   _Alternative payload test with `UNION SELECT`_

6. ![sqli-h-6.png](/sqli-h-6.png)  
   _HTML/DOM inspection confirming no reflected output_
