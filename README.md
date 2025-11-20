# Task 4: Setup and Use a Firewall (UFW)

## 🚩 Objective
To configure and test basic firewall rules to allow or block traffic using **UFW (Uncomplicated Firewall)** on Linux. This task demonstrates network traffic filtering, port security, and firewall management.

## 🛠️ Tools Used
* **Operating System:** Linux (Kali/Debian)
* **Firewall Tool:** UFW (Uncomplicated Firewall)
* **Target Ports:** SSH (Port 22), Telnet (Port 23)

---

## 📸 Proof of Work
*(Upload your screenshot to the repo and name it `screenshot.jpg`)*

![Firewall Configuration Screenshot](screenshot.jpg)

*Description: Screenshot showing the creation of rules, verification of status, testing the block, and cleanup.*

---

## 📝 Execution Steps (Combined)

### The Firewall Configuration and Testing Process

I began by installing UFW and setting a foundational rule to **allow SSH (Port 22)** access to prevent being locked out, then enabled the firewall service.

Next, I implemented the required security rule by running `sudo ufw deny 23/tcp` to **block inbound Telnet traffic**.

To **verify the rules**, I used `sudo ufw status numbered`, which confirmed that Port 22 was ALLOWED and Port 23 was DENIED.

For **testing**, I executed `telnet localhost 23`. The resulting **"Connection refused"** message confirmed the rule was functioning correctly.

Finally, the rule was removed for **cleanup** by running `sudo ufw delete 4` to restore the system state.

```bash
# Installation and Setup
sudo apt install ufw -y
sudo ufw allow 22/tcp
sudo ufw enable

# Rule Implementation and Verification
sudo ufw deny 23/tcp
sudo ufw status numbered

# Testing and Cleanup
telnet localhost 23
sudo ufw delete 4
