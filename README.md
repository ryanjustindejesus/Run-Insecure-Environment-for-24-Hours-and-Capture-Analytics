<h1>Run Insecure Environment for 24 Hours and Capture Analytics</h1>

- <b>This tutorial outlines the configuration of capturing our insecure environment map analytics after leaving it running for 24 hours</b>

<h2>Environments and Technologies Used</h2>

- <b>Microsoft Azure</b> 
- <b>Microsoft Sentinel</b>
- <b>Log Analytics Workspace</b>

<h2>Operating Systems</h2>

- <b>Windows 10</b>

<h2>Configuration Steps</h2>

## Metrics Before Hardening / Security Controls

- <b>The following table shows the metrics we measured in our insecure environment for 24 hours:</b>
- <b>Start Time   2024-10-01 08:48:43</b>
- <b>Stop Time    2024-10-02 08:48:43</b>

| Metric                   | Count
| ------------------------ | -----
| SecurityEvent            | 14336
| Syslog                   | 1610
| SecurityAlert            | 0
| SecurityIncident         | 162
| AzureNetworkAnalytics_CL | 1386

## Attack Maps Before Hardening / Security Controls

![windows-rdp-auth-fail](https://github.com/user-attachments/assets/e8294af7-fdea-40e1-ba22-9a141f5f0f01)
- <b>Navigate to Microsoft Sentinel and click workbooks</b>
- <b>Click windows-rdp-auth-fail and capture the map analytics from the last 24 hours</b>
- <b>Repeat the same process for your linux-ssh and nsg-malicious map analytics</b>

![linux-ssh-auth-fail](https://github.com/user-attachments/assets/73c2afab-5799-4489-834d-d933472bc70c)


![nsg-malicious-allowed-in](https://github.com/user-attachments/assets/feafa721-e614-436c-bcdf-2b13560c2637)

- <b>Navigate to Log Analytics Workspace and use these queries to determine the metrics of our insecure environment for the last 24 hours</b>
- <b>SecurityEvent (Windows Event Logs)</b>
```
SecurityEvent
| where TimeGenerated >= ago(24h)
| count
```

- <b>Syslog (Linux Event Logs)</b>
```
Syslog
| where TimeGenerated >= ago(24h)
| count
```

- <b>SecurityAlery (Microsoft Defender for Cloud)</b>
```
SecurityAlert
| where DisplayName !startswith "CUSTOM" and DisplayName !startswith "TEST"
| where TimeGenerated >= ago(24h)
| count
```

- <b>SecurityIncident (Incidents created by Sentinel)</b>
```
SecurityIncident
| where TimeGenerated >= ago(24h)
| count
```

- <b>AzureNetworkAnalytics_CL (Malicious Flows allowed into our honeynet)</b>
```
AzureNetworkAnalytics_CL 
| where FlowType_s == "MaliciousFlow" and AllowedInFlows_d > 0
| where TimeGenerated >= ago(24h)
| count
```
