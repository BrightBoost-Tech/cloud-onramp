# Part 1 — Your First Virtual Machine (VM)
- Video A — First VM (≤5 min): [assets/videoA-first-vm.mp4](assets/videoA-first-vm.mp4)

**Audience:** First-time cloud users  
**Goal:** Create a small Linux VM, connect with SSH, and run a short Python “hello cloud” script.  
**Time:** 10–20 minutes  
**Cost:** VMs can incur charges. Stop/terminate the VM when you finish.

---

## Prerequisites
- A cloud account (AWS, GCP, Azure, or similar)
- An SSH key pair (public/private)
- Terminal access (macOS/Linux, Windows + WSL)

---

## Steps

### 1) Create a Linux VM
Create the smallest Linux VM available on your provider (Ubuntu/Debian works).  
Open inbound **port 22 (SSH)** to **your IP only**.  
Write down the **public IP** and the image’s **default username**.

Common usernames:
- Ubuntu → `ubuntu`
- Amazon Linux → `ec2-user`
- Debian → `admin` (sometimes `debian`)

### 2) Connect with SSH
Set key permissions (macOS/Linux/WSL):
```bash
chmod 600 mykey.pem
Connect:

bash
Copy code
ssh -i mykey.pem <username>@<VM_PUBLIC_IP>
3) Run the hello script
If Python is missing (Ubuntu/Debian):

bash
Copy code
sudo apt-get update -y && sudo apt-get install -y python3
Run:

bash
Copy code
python3 - <<'PY'
import platform, sys
print("hello, cloud")
print(platform.platform())
print(sys.version)
PY
Verify (success criteria)
You should see:

php-template
Copy code
hello, cloud
Linux-<version-and-distro>
3.11.x (…)
Troubleshooting
Permission denied (publickey): chmod 600 mykey.pem

SSH times out: allow port 22 from your IP in the security group/firewall

Wrong username: try ubuntu, ec2-user, or admin

Cleanup
Stop or terminate the VM from your provider’s console/CLI to avoid charges.

Check your understanding
Pre

True/False — SSH requires port 22 to be open.

Multiple choice — Which command starts a secure shell session?
A) ftp B) telnet C) ssh D) scp

Post

True/False — Terminating the VM prevents further charges.

Short answer — Which Python module prints OS details in this guide?

<details> <summary>Answer key</summary>
Pre: 1) True 2) C
Post: 1) True 2) platform

</details> ```