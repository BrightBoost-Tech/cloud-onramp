# Cloud On-Ramp 🚀

**Audience:** First-time cloud builders  
**Goal:** Provide a simple, three-part path to get from zero → VM → GPU → Kubernetes Job, with clear steps, success criteria, and demos.  
**Estimated total time:** ~45–60 minutes  

---

## 📋 Quick Start
- [Quickstart Card (PDF)](quickstart-card.pdf) — 1-page overview  
- Video A — First VM (≤5 min): [assets/videoA-first-vm.mp4](assets/videoA-first-vm.mp4)  
- Video B — First K8s Job (≤5 min): [assets/videoB-k8s-job.mp4](assets/videoB-k8s-job.mp4)  

---

## 🧩 The Series

### [Part 1 — First VM](01-first-vm/README.md)
- Create a Linux VM in the cloud  
- Connect with SSH  
- Run a simple Python “hello cloud” script  
- **Verify:** greeting, OS info, Python version  

### [Part 2 — First GPU Job](02-first-gpu-job/README.md)
- Launch a GPU VM  
- Verify drivers with `nvidia-smi`  
- Run a tiny PyTorch CUDA check  
- **Verify:** `cuda available: True`  

### [Part 3 — First Kubernetes Job](03-first-orchestrated-job/README.md)
- Use `kind` to create a local Kubernetes cluster  
- Apply a batch Job manifest  
- Check logs for success message  
- **Verify:** `hello, k8s from a Job`  

---

## 📊 Metrics & Pre/Post Checks
See [metrics.md](metrics.md) for:  
- **Time-to-first-success (TTFS)** per part  
- Pre/post knowledge check questions  

---

## 🧹 Cleanup Reminder
Always **stop or terminate** cloud VMs when finished to avoid charges.  
Delete kind clusters locally to free resources.

---

## 🔖 License
This project is licensed under the [MIT License](LICENSE).
