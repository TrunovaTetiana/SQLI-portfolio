# SQL Injection — DVWA (Medium Level)

## Vulnerability: SQL Injection (Medium Level)
The objective of this test was to exploit a SQL injection vulnerability by injecting a payload directly into a manipulated `<select>` HTML dropdown using browser dev tools.

---

## Injection Payload Used

```
1 UNION SELECT user, password FROM users LIMIT 2,1 --
```

---

## Steps Performed

1. Opened the vulnerable SQL Injection page on DVWA (medium level).
2. Opened Developer Tools (F12) and found the `<select name="id">` block.
3. Manually injected a custom `<option>` value with SQL injection payload.
4. Selected the injected option from the dropdown.
5. Clicked "Submit" and confirmed the database returned credentials.

---

## Screenshots

1. Modifying the `<select>` HTML in DevTools  
   ![sqli-medium-1](/SQLI-medium-1.png)

2. Interface before selecting payload  
   ![sqli-medium-2](/SQLI-medium-2.png)

3. Injection result displayed — login and password hash  
   ![sqli-medium-3](/SQLI-medium-3.png)

4. Dropdown successfully modified — new injected options  
   ![sqli-medium-4](/SQLI-medium-4.png)

---

## Recommendations

- Never trust client-side input — sanitize server-side.
- Use prepared statements with parameterized queries.
- Implement Web Application Firewall (WAF) for additional protection.
- Restrict DB permissions — avoid exposing `user` and `password` tables.

---

## Tester

**Name**: Tetiana Trunova  
**Environment**: DVWA on Ubuntu VM, tested from Kali Linux  
**Browser**: Firefox with DevTools

---

## Conclusion

This test confirms that the DVWA (Medium Level) SQL Injection is exploitable via manipulation of HTML form elements. Bypassing the input restriction through DevTools allowed successful SQL payload injection and data exfiltration.
