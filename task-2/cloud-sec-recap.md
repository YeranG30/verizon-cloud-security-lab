# Task 2 – Cloud-Based Application Security (Verizon Industry Lab)

##  Objective

Conduct research and provide insights on how to secure cloud-native applications across three key layers: **Network Security**, **Application Security**, and **Data Security**. This is in support of the Verizon CCE team’s ongoing development and testing of the internal VPN service, Sasha.

---

##  1. Network Security

Focuses on protecting cloud applications by securing traffic flow using edge-layer controls and infrastructure policies.

###  Key Strategies

- Implement **firewall rules** at ingress and egress points to allow only known ports, protocols, and source IPs.
- Use **TLS/SSL encryption** for all traffic in transit to protect data integrity and confidentiality.
- Deploy **DDoS protection mechanisms** (e.g., AWS Shield, Azure DDoS Protection) to absorb or mitigate volumetric attacks.
- Enable **WAF (Web Application Firewall)** to filter malicious HTTP requests targeting known vulnerabilities (e.g., SQLi, XSS).
- Configure **security groups** and **network ACLs** (Access Control Lists) to isolate workloads by environment (dev, staging, prod).

---

##  2. Application Security

Ensures that application logic and APIs are resilient to abuse and follow secure development practices.

###  Key Strategies

- Enforce **authentication and authorization** using OAuth2, OpenID Connect, or SAML-based IAM.
- Validate all inputs to prevent **injection flaws** (e.g., SQLi, command injection).
- Scan **container images and dependencies** for known CVEs using tools like Trivy or Grype.
- Integrate **SAST/DAST** into CI/CD pipelines to detect insecure code patterns and runtime behavior.
- Follow **principle of least privilege (PoLP)** for every user, API key, and container process — minimizing blast radius.
- Harden application endpoints to prevent **IDOR**, CSRF, and broken access control issues.

---

##  3. Data Security

Safeguards data at rest and in transit using cryptographic, access management, and redundancy controls.

###  Key Strategies

- Use **AES-256** or equivalent encryption for data at rest (volumes, S3, DB).
- Enforce **TLS 1.2+** for encryption in transit (HTTPS, mTLS).
- Implement **IAM policies** to enforce fine-grained access control at the resource level.
- Store secrets in secure vaults (e.g., **HashiCorp Vault**, **AWS Secrets Manager**).
- Enable automated **database backups** and **disaster recovery plans** for data availability.

---

##  Summary

By understanding and implementing security controls at each layer of a cloud-native stack, we ensure that applications like Sasha are resilient, compliant, and production-ready. These insights were drawn from practical research, internal documentation, and Verizon’s secure design expectations.

---

## 📎 Sources Consulted

- OWASP Cloud-Native Security Top 10
- AWS Well-Architected Security Pillar
- Google Cloud Architecture Framework – Security
- Verizon Cloud Security Training Modules (Forage)
