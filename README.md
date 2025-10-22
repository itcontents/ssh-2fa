PLEASE SUBSCRIBE TO ALL MY CHANNEL

- youtube.com/@itcontents
- tiktok.com/@itcontents
- facebook.com/itcontents
- instagram.com/itcontents1

## 📦 Step 1: Install Google Authenticator PAM Module

### Debian/Ubuntu

sudo apt update
sudo apt install libpam-google-authenticator

### RHEL/CentOS/Fedora
bash
sudo dnf install google-authenticator
📲 Step 2: Configure Authenticator for Your User
Run the setup command:

google-authenticator

Choose time-based tokens y
Save your secret key, emergency codes, and QR code

Scan the QR code with your Authenticator app (Google Authenticator, Authy, etc.)

🔧 Step 3: Configure PAM for SSH
Edit the PAM SSH file:
sudo nano /etc/pam.d/sshd

Add this line at the top:
auth required pam_google_authenticator.so

⚙️ Step 4: Update SSH Daemon Configuration
Edit the SSH config:
sudo nano /etc/ssh/sshd_config

Ensure these lines are set:

ChallengeResponseAuthentication yes
UsePAM yes
PasswordAuthentication yes  # Optional: keep if using password + 2FA

Restart SSH:
sudo systemctl restart sshd

Step 5: Test SSH Login
ssh youruser@yourserver


✅ Optional: Harden Further
Disable password auth (use SSH keys + 2FA):

PasswordAuthentication no # make sure you have you key before you turn this off

📌 Notes
Works with any TOTP app: Google Authenticator, Authy, Microsoft Authenticator

Backup your emergency codes securely

Use google-authenticator -t -d -f -r 3 -R 30 -w 3 for advanced config



```
