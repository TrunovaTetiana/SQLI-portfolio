# 🧠 SQL Injection Portfolio by Tetiana Trunova

This repository contains my **practical portfolio on Web Pentesting**, focused on **SQL Injection (SQLi)** vulnerabilities, from **Low** to **High** security levels in DVWA.  
It includes detailed attack attempts, payloads, screenshots, testing environments, and **defense analysis**.

---

## 📁 Structure

- 🔽 **Low Level SQL Injection**
- 🟡 **Medium Level SQL Injection**
- 🔒 **High Level SQL Injection**
- 💡 Defense & Mitigation Notes
- 📸 Screenshots with Burp Suite / Browser Inspector
- 🧪 PoC Results + Recommendations

---

## 🛠️ Tools & Environment

- 🐱‍💻 Kali Linux (attacker machine)
- 🐧 Ubuntu with DVWA (target)
- 🧰 Burp Suite
- 🌐 Firefox + Chrome for browser testing
- 🧾 Custom payloads
- 🖥️ VS Code + GitHub

---

## ✅ Completed Scenarios

- `SQLi - Low` – Success: classic injection
- `SQLi - Medium` – Success: bypass via crafted payload
- `SQLi - High` – ❌ Defense confirmed: likely prepared statements + type filtering

All screenshots confirming PoC results are located in the `screenshots/` folder and grouped by test level.

---

## 📸 Screenshots Preview

- DVWA interface with SQL Injection levels
- Burp Suite intercepted requests
- Payload testing (URL / Form)
- Blank responses, filtered input
- HTML/DOM inspection
- No data leaks confirmed on High

---

## 🔐 Security Analysis (High Level)

> DVWA at High level successfully neutralizes all classic SQL injection attempts, likely due to:
- Usage of **`bindParam()`**
- Strict **input type validation**
- **Sanitized** and **parameterized queries**
- Blocked `UNION`, `OR`, arrays, headers, and error-based techniques

✅ *This confirms effective defense at the application layer.*

---

## 👩‍💻 About Me

**Tetiana Trunova**  
Cybersecurity Specialist & Web Pentester  
📍 Warsaw, Poland  

- 🎓 Certified in Cybersecurity  
- 🏅 TryHackMe Learner  
- 💼 Open to Bug Bounty, freelance, and junior security roles  

[![TryHackMe](https://tryhackme-badges.s3.amazonaws.com/TetianaTrunova.png)](https://tryhackme.com/p/TetianaTrunova)  
🔗 [LinkedIn: Tetiana Trunova](https://www.linkedin.com/in/tetiana-trunova/)  
🔗 [GitHub: TrunovaTetiana](https://github.com/TrunovaTetiana)

---

## 📌 Notes

> Full SQL Injection testing process documented step-by-step in Markdown reports, with attack payloads, test results, screenshots, and analysis of defenses.  
Each level includes:
- URL and form-based payload injection
- Observed behavior
- Defense mechanisms and bypass attempts
- Conclusion and recommendations

---

## 📂 Repository Content

- `/screenshots` – Screenshots from Burp Suite and browser
- `/sqli-high.md`, `/sqli-medium.md`, etc. – Markdown reports
- `README.md` – This file

---

## 📢 License

MIT License – Free to use for educational and portfolio purposes.

---
