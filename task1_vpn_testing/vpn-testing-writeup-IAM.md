# Task 1 – VPN Testing: Sasha Enterprise Service

##  Objective

Evaluate **Sasha**, Verizon’s enterprise VPN service built on Squid proxy servers, for key **cloud-native traits** including **resilience**, **elasticity**, **fault tolerance**, and **least privilege enforcement**.

---

## Test Methodology

Using a Verizon-developed Python CLI tool (`cloud-app.py`), we simulated failures and analyzed internal behavior to determine cloud-native compliance.

---

### 1. Resilience (Self-Healing)

**Test Action:**
```bash
kill squid-proxy-71222
```

**Expected Outcome:**
- Service detects pod termination
- Automatically replaces terminated pod

**Observed Output:**
```
Application is ***Scaling Up*** with a total of 0/1 running pods.
POD_NAME            STATUS              READY       AGE
squid-proxy-87832   Running             1/1         4s
```

**Conclusion:** Service recovers autonomously, validating self-healing design.

---

###  2. Elasticity (Horizontal Scaling)

**Test Action:**
```bash
scale 6
```

**Observed Output:**
```
Application is ***Running*** with a total of 6/6 running pods.
```

**Conclusion:** Sasha dynamically scales pods based on load commands — a required characteristic of cloud-native services.

---

###  3. Least Privilege Validation

**Test Action:**
```bash
get-user squid-proxy-02379
```

**Expected Principle:**
Service pods should run with restricted, non-root user privileges.

**Observed Output:**
```
User running: squidvpnsvc (UID: 1001)
```

 **Conclusion:** Service operates under a non-root identity, following the principle of least privilege.

---

##  Code Review Insights

Key excerpt from the CLI interface logic (`cloud-app.py`):

```python
def get_user(pod):
    return f"User running: {pod.user} (UID: {pod.uid})"
```

**Insight:**  
Service integrates user ID retrieval to validate container runtime context, allowing internal checks for privilege escalation risks.

---

##  Tools Used

- Python 3.7+
- Verizon internal CLI testing suite (`cloud-app.py`)
- Manual command-line testing (Windows CMD & Bash)

---

##  Conclusion

Sasha meets essential cloud-native principles:
-  Resilience: automated failover and pod replacement
-  Elasticity: on-demand horizontal scaling
-  Least Privilege: containers run as non-root

These behaviors confirm Sasha's readiness for secure, scalable deployment within Verizon's internal and external cloud platform.
