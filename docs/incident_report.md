# Incident Report: SSH Brute Force Detection

## Project Overview
This report summarizes the investigation conducted on SSH authentication logs aimed at detecting brute force attacks using Splunk. The goal was to identify patterns of repeated failed login attempts, pinpoint attacking IPs, and determine temporal trends to inform SOC response strategies.

---

## 1. Total Failed Login Attempts
- **Counted failed SSH login attempts over the log period:**  
  `197587`  
- This number represents all “Failed password” events detected, indicating potential brute force activity.

---

## 2. Top Source IPs
The following IP addresses were identified as the most frequent sources of failed login attempts:

| Rank | Source IP       | Number of Failed Attempts | Percentage of Total |
|-------|----------------|--------------------------|--------------------|
| 1     | `59.63.188.30`  |     `28766`             | `14.56%`           |
| 2     |`183.63.110.206` |     `17340`             | `8.78%`            |
| 3     |`183.238.178.195`|     `14519`             | `7.35&`             |

- These IPs account for approximately `31%` of all failed login attempts.
- Such concentrated attack activity indicates possible targeted brute force or botnet behavior.

---

## 3. Most Eventful Day
- The day with the highest volume of failed login events was:  
  **`January 3`**  
- Number of failed attempts on this day: `31843`  
- This spike suggests a coordinated attack or scanning activity concentrated during this timeframe.
  
---

## 4. Temporal Trends and Patterns
- Failed login attempts showed `<rising/declining/steady>` trend over the analyzed period.
- Notable bursts occurred during `<specific hours or dates>` suggesting possible scheduled automated attacks.
  
---

## 5. Additional Observations
- **Username targeting:** Attempts were made mostly against common usernames such as `root`, `admin`, and `user`.
- **Port analysis:** All attacks were observed on SSH default port 22.
- **Failed vs Successful Logins:** Ratio of failed to successful authentications was approximately `1,197:1`, indicating significant unauthorized access attempts.

---

## 6. Recommendations
- **Implement account lockout policies** after `5` failed attempts within `1` minute.
- **Enable multi-factor authentication** (MFA) to harden access to SSH services.
- **Apply IP blacklisting or firewall rules** blocking the top malicious IPs temporarily.
- **Monitor for similar activity patterns going forward** using Splunk alerts and dashboards developed.
- **Conduct user awareness training** about avoiding weak passwords and report suspicious login prompts immediately.

---

## 7. Conclusion
This investigation highlighted key brute force patterns identifiable through log analysis and Splunk SPL queries. Detecting and profiling attacker IPs, correlating events temporally, and documenting findings builds SOC readiness to respond swiftly and mitigate brute force threats effectively.

---

**Prepared by:** Yakshvardhan Jaitely  
**Date:** `8 August 2025`

---

### Appendix
- Dashboard screenshots (refer to /screenshots folder)

---

