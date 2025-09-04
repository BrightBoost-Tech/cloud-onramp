# Part 2 — Your First GPU Job

**Audience:** First-time cloud users  
**Goal:** Launch a single-GPU VM, verify the driver, and run a tiny CUDA check.  
**Time:** 15–30 minutes  
**Cost:** GPU VMs cost more. Stop/terminate when finished.

---

## Prerequisites
- A cloud account with access to a **GPU** VM type (or skip to the CPU fallback note)
- SSH access (key + security group for port 22)

> **No GPU?** You can read this part and still proceed to Part 3. The code below prints whether CUDA is available on your VM.

---

## Steps

### 1) Create a GPU VM
Create the smallest available GPU VM on your provider. Prefer an image that includes NVIDIA drivers/CUDA.  
Write down:
- Public IP
- Default username for the image

### 2) Connect with SSH
```bash
ssh -i mykey.pem <username>@<VM_PUBLIC_IP>
3) Verify the GPU driver
bash
Copy code
nvidia-smi
You should see a table with the GPU model and driver version.

4) Run a CUDA check (with PyTorch)
If PyTorch isn’t installed:

bash
Copy code
python3 -m pip install --user torch --index-url https://download.pytorch.org/whl/cpu
The CPU wheel installs even without CUDA; the code still reports cuda available: False if no GPU is visible.

Run:

python
Copy code
python3 - <<'PY'
try:
    import torch
    print("cuda available:", torch.cuda.is_available())
    if torch.cuda.is_available():
        print("gpu:", torch.cuda.get_device_name(0))
        x = torch.randn(1024, 1024, device="cuda")
        y = x @ x.T
        print("result:", y.shape)
except Exception as e:
    print("error:", e)
PY
Verify (success criteria)
nvidia-smi prints GPU info.

Python prints cuda available: True and shows a GPU name.

If you used a CPU-only image or no GPU is present, cuda available: False is expected.

Troubleshooting
nvidia-smi: command not found — Use a GPU image that includes drivers, or install NVIDIA driver/CUDA from your provider’s docs.

cuda available: False but you expect True — Driver/CUDA toolkit mismatch; reboot after driver install; confirm the image supports your VM type.

SSH timeout — Ensure port 22 is open to your IP.

Cleanup
Stop/terminate the GPU VM immediately to avoid charges.

Check your understanding
Pre

True/False — nvidia-smi verifies the NVIDIA driver.

Multiple choice — Which Python call reports CUDA availability?
A) torch.has_cuda() B) torch.cuda.is_available() C) torch.cuda.ok() D) torch.use_cuda()

Post

Short answer — Name one reason torch.cuda.is_available() may return False.

True/False — You should stop or terminate a GPU VM when you finish.

<details> <summary>Answer key</summary>
Pre: 1) True 2) B
Post: 1) e.g., driver mismatch, no GPU present, CUDA not installed, permissions; 2) True

</details> ```