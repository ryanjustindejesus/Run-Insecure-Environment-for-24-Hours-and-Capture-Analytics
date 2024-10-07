<h1>Run Insecure Environment for 24 Hours and Capture Analytics</h1>

- <b>This tutorial outlines the configuration of capturing our insecure environment map analytics after leaving it running for 24 hours</b>

<h2>Environments and Technologies Used</h2>

- <b>Microsoft Azure</b> 
- <b>Microsoft Sentinel</b>
- <b>Log Analytics Workspace</b>

<h2>Operating Systems</h2>

- <b>Windows 10</b>

<h2>Configuration Steps</h2>

- <b>At this point, we have left our insecure virtual machines running for at least 24 hours</b>

![windows-rdp-auth-fail](https://github.com/user-attachments/assets/e8294af7-fdea-40e1-ba22-9a141f5f0f01)
- <b>Navigate to Microsoft Sentinel and click workbooks</b>
- <b>Click windows-rdp-auth-fail and capture the map analytics from the last 24 hours</b>
- <b>Repeat the same process for your linux-ssh and nsg-malicious map analytics</b>

![linux-ssh-auth-fail](https://github.com/user-attachments/assets/73c2afab-5799-4489-834d-d933472bc70c)


![nsg-malicious-allowed-in](https://github.com/user-attachments/assets/feafa721-e614-436c-bcdf-2b13560c2637)
