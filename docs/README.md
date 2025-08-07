# Splunk SSH Brute Force Detection Project

## Project Overview

This project demonstrates detection and analysis of SSH brute force attacks using Splunk. By ingesting authentic SSH authentication logs from a publicly available dataset, we simulate a real-world SOC analyst’s workflow to identify suspicious login attempts, aggregate failed authentications by source IP, and visualize attack trends.

This repository contains raw log data, Splunk search queries (SPL) crafted for brute force detection, dashboard screenshots visualizing key incident patterns, and a concise incident report summarizing findings and investigative insights.

## Data Source

- The SSH logs used in this project are downloaded from the Kaggle dataset **LogHub SSH Log Data**:  
  [https://www.kaggle.com/datasets/omduggineni/loghub-ssh-log-data](https://www.kaggle.com/datasets/omduggineni/loghub-ssh-log-data?resource=download)
- The logs capture detailed authentication events including successful logins, failed password attempts from various IP addresses, timestamps, ports, and usernames.

## Project Structure

/splunk-bruteforce-project
│
├── README.md # This project overview, instructions, and tips
├── /data # Raw SSH brute force log files (e.g., ssh.log)
├── /search_queries # Splunk SPL queries for analysis and detection
│ ├── failed_login_search.spl
│ ├── top_ips_count.spl
│ └── alert_rule_example.spl
├── /dashboard_screenshots # Screenshots of Splunk visualizations and dashboards
│ ├── failed_logins_chart.png
│ └── top_ips_column_chart.png
├── incident_report.md # One-page summary of investigation, detections, and relevance
└── LICENSE # License file 

## How to Use This Project

### 1. Upload Data to Splunk

- Launch Splunk Web interface (local installation or cloud).
- Navigate to **Settings → Add Data → Upload**.
- Select the log file from `/data/ssh.log`.
- Set source type to `SSH.log` or create a custom type if needed.
- Assign to an index (i assigned it to "main" index but you can use whatever you like).
- Complete the upload and verify indexing by searching:


### 2. Run Search Queries

- Use the provided SPL queries below to extract key fields and analyze brute force activity:
- Extract source IP addresses from raw logs.
- Aggregate and count failed login attempts by IP and time.
- Identify and highlight suspicious IPs exceeding failure thresholds.
- Example SPL snippet to extract IP and count failed attempts:
- index=security sourcetype=syslog Failed password
    | rex "from (?<src_ip>\d{1,3}(?:\.\d{1,3}){3})"
    | stats count by src_ip
    | where count > 5

### 3. Build Dashboards

- Save key searches as dashboard panels visualizing:
- Number of failed attempts by source IP (column chart).
- Failed login trends over time (time chart).
- Tables listing top attacking IPs.
- Use screenshots in `/dashboard_screenshots` for reference or inclusion in reports.

### 4. Investigate and Report

- Use the dashboards and queries to investigate patterns indicating brute force attacks.
- Prepare incident documentation (see `incident_report.md`) outlining findings, analysis steps, and implications for a SOC environment.
- This report demonstrates your ability to detect, triage, and communicate security events effectively.

## Prerequisites

- Splunk Enterprise or Splunk Cloud instance (free trial or installed locally).
- Basic familiarity with Splunk Search Processing Language (SPL).
- Access to the logs in `/data`.

## Why This Project Matters

Detecting brute force attacks is a core responsibility of SOC analysts. This project simulates real-world conditions where attackers attempt password guessing on SSH services, and analysts must sift through voluminous logs to find malicious activity. Building dashboards, writing queries, and summarizing threats develop critical skills demanded by cybersecurity employers.

## References

- Kaggle LogHub SSH Log Data: https://www.kaggle.com/datasets/omduggineni/loghub-ssh-log-data
- Splunk Documentation: https://docs.splunk.com/

---

Feel free to explore, customize queries, and extend this project as you build your SOC analyst portfolio.

---

**Author:** Yakshvardhan Jaitely  
**Date:** August 2025

