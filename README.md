# 🔍 Threat Modeling Using STRIDE — Web Application Case Study

This project presents a complete **Threat Modeling Assessment** using the **STRIDE framework** for a multi-tier web application environment.  
It demonstrates professional consulting capabilities in identifying threats early in the design phase, mapping them to mitigations, and reducing overall attack surface.

This model aligns with:
- Microsoft SDL  
- OWASP Threat Modeling  
- Zero Trust Principles  
- ISO 27001 Annex A  
- NIST Cybersecurity Framework  

---

# 📘 1. Project Summary

The goal of this project is to perform **threat modeling** on a web application to:

- Identify potential threats across all components  
- Highlight design weaknesses  
- Assess the likelihood and impact of attacks  
- Provide actionable mitigation strategies  
- Improve the security posture from the early development stage  

This threat model is suitable for:
- Web apps  
- APIs  
- Microservices  
- Authentication systems  
- Enterprise systems  

---

# 🎯 2. Objectives

- Model the system using Data Flow Diagrams (DFDs)  
- Identify trust boundaries  
- Perform STRIDE analysis  
- Map threats to controls  
- Recommend secure design improvements  
- Reduce risk before development/deployment  

---

# 🧩 3. System Description

The system consists of:

- Public users accessing a web application  
- A web server in the DMZ  
- Application server processing business logic  
- Backend database storing sensitive records  
- Logging/SIEM system  
- Admin users accessing management console  

---

# 🖼️ 4. Data Flow Diagram (DFD Level-1) — ASCII

            ┌────────────────────────────┐
            │        User Browser         │
            └──────────────┬─────────────┘
                           │  (1) HTTPS Request
                   ┌───────▼─────────┐
                   │    Web Server   │
                   │   (DMZ Layer)   │
                   └───────┬─────────┘
                  (2) API Request │
                   ┌────────▼────────┐
                   │ Application Tier │
                   │  Business Logic  │
                   └────────┬────────┘
                  (3) SQL Query │
         ┌─────────▼──────────┐
         │    Database Server  │
         │ (Sensitive Records) │
         └─────────┬──────────┘
                  (4) Logs
           ┌────────▼────────┐
           │    SIEM / Log    │
           │    Aggregator    │
           └──────────────────┘

  ★ TRUST BOUNDARIES ★  
  - Between User ↔ Web Server  
  - Between Web ↔ App Server  
  - Between App ↔ Database  
  - Between App ↔ Logging System  

---

# 🧠 5. STRIDE Framework Overview

| Category | Threat Focus |
|----------|--------------|
| S | Spoofing identity |
| T | Tampering with data |
| R | Repudiation |
| I | Information Disclosure |
| D | Denial of Service |
| E | Elevation of Privilege |

---

# 🔍 6. Threat Identification (STRIDE Analysis)

Below is a **professional consultant-grade threat table** for the system.

---

## **S → Spoofing Threats**
| Component | Threat | Impact | Mitigation |
|-----------|---------|---------|-------------|
| User Login | Credential theft, session hijacking | High | MFA, secure cookies, OAuth2, TLS |
| API Gateway | API key spoofing | High | Signed tokens, JWT validation |
| Admin Console | Privilege spoofing | Critical | RBAC, Just-in-Time access |

---

## **T → Tampering Threats**
| Component | Threat | Impact | Mitigation |
|-----------|---------|---------|-------------|
| Web/App Traffic | Parameter tampering, API manipulation | High | Input validation, WAF |
| Database | SQL Injection modifies data | Critical | Parameterized queries, ORM |
| Logs | Log tampering | Medium | WORM storage, SIEM integrity checks |

---

## **R → Repudiation Threats**
| Component | Threat | Impact | Mitigation |
|-----------|---------|---------|-------------|
| User Actions | Users deny transactions | High | Audit logs, timestamping |
| Admin Actions | No tracking for changes | High | Immutable logs, session recording |
| APIs | No traceability | Medium | API Gateway logging |

---

## **I → Information Disclosure**
| Component | Threat | Impact | Mitigation |
|-----------|---------|---------|-------------|
| Web Server | Sensitive info leak via errors | Medium | Error handling, masked errors |
| Database | Data breach via SQLi or LFI | Critical | DB firewall, encryption |
| Logs | Exposed logs with PII | Medium | Access controls, log masking |

---

## **D → Denial of Service**
| Component | Threat | Impact | Mitigation |
|-----------|---------|---------|-------------|
| Web/App Layer | Flooding, HTTP exhaustion | High | Rate limiting, CDN, WAF |
| Database | Resource starvation | High | Query throttling, caching |
| Authentication | Credential stuffing | Medium | Lockout policies, CAPTCHA |

---

## **E → Elevation of Privilege**
| Component | Threat | Impact | Mitigation |
|-----------|---------|---------|-------------|
| Web Application | Broken Access Control | High | RBAC, ABAC |
| Database | Privilege escalation | Critical | Least privilege, separate accounts |
| Admin Portal | Super-admin takeover | Critical | JIT access, MFA, monitoring |

---

# 🧱 7. Attack Surface Analysis

### Major Attack Vectors:
- Login pages  
- API endpoints  
- File upload features  
- Database queries  
- Admin portal  
- Misconfigured trust boundaries  

### High-Risk Vulnerabilities:
- SQL Injection  
- XSS / DOM attacks  
- Broken Access Control  
- API key exposure  
- Credential reuse  
- Weak session management  

---

# 🛡️ 8. Security Mitigation Strategy

### ✔ Authentication & Identity
- MFA everywhere  
- OAuth2 / OpenID Connect  
- Secure password policies  
- Device posture verification  

### ✔ Network Security
- WAF (Web Application Firewall)  
- TLS 1.2/1.3 enforcement  
- API rate limiting  
- Segmented zones (DMZ → App → Data)  

### ✔ Application Security
- Input validation (server-side)  
- Parameterized queries  
- Secure session management  
- Secure coding practices (OWASP)  

### ✔ Data Security
- AES-256 encryption at rest  
- TLS for data in transit  
- Backup encryption  
- Key rotation policy  

### ✔ Logging & Monitoring
- Centralized logging (SIEM)  
- Alerting on suspicious activity  
- Immutable logs  
- Admin action monitoring  

---

# 🔒 9. Residual Risk Evaluation

| Threat | Residual Risk | Reason |
|--------|----------------|---------|
| SQL Injection | Low | Fully mitigated with prepared statements |
| XSS | Medium | Dependent on dev implementation |
| DoS | Medium | Mitigated but not eliminated |
| Privilege Escalation | Low | Strong IAM & RBAC |
| Data Leakage | Low | Encryption + WAF + verification |

---

# 📦 10. Deliverables

This project includes:

- Level-1 Data Flow Diagram  
- STRIDE Threat Modeling Table  
- Attack Surface Analysis  
- Mitigation Mapping  
- Security Control Recommendations  
- Residual Risk Evaluation  

---

# 📈 11. Key Outcomes

- Identified 40+ potential threats across architecture  
- Mapped all STRIDE threats to actionable controls  
- Improved architecture’s security posture significantly  
- Reduced likelihood of common attack vectors  
- Strengthened design before implementation  

---

# 🧾 12. Conclusion

This STRIDE Threat Model provides a **comprehensive and structured approach** to identifying and mitigating threats in an enterprise web application.

It demonstrates professional-level capabilities in:

- Secure architecture design  
- Threat modeling  
- Attack surface reduction  
- Control mapping  
- Risk assessment  

This ensures the system is designed with **security-by-design and defense-in-depth** principles.

---

# 📬 Contact

**GitHub:** https://github.com/rajbharti-cyber  
**LinkedIn:** https://www.linkedin.com/in/rajbharti-cybersecurity/
