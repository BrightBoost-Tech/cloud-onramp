# Part 3 — Your First Kubernetes Job (with kind)

**Audience:** First-time cloud users  
**Goal:** Run a one-off batch Job on a local Kubernetes cluster using kind.  
**Time:** 10–20 minutes  
**Cost:** Local only (no cloud charges).

---

## Prerequisites
- Docker Desktop running with **WSL Integration** enabled for Ubuntu
- `kubectl` and `kind` installed (verified in Phase 1)

---

## Steps

### 1) Start a kind cluster
```bash
kind create cluster --name onramp --wait 120s
kubectl config use-context kind-onramp
kubectl get nodes
2) Apply the Job manifest
bash
Copy code
kubectl apply -f hello-job.yaml
kubectl wait --for=condition=complete job/hello-job --timeout=90s
3) View logs
bash
Copy code
kubectl logs job/hello-job
Verify (success criteria)
You should see:

css
Copy code
hello, k8s from a Job
Troubleshooting
“docker not found / cannot connect to daemon”
Open Docker Desktop → Settings → General: Use the WSL 2 based engine.
Settings → Resources → WSL Integration: toggle Ubuntu ON. Then restart Docker Desktop.

context "kind-onramp" not found
Run kind create cluster --name onramp again, then kubectl config get-contexts and kubectl config use-context kind-onramp.

Pod stuck in ImagePullBackOff
kubectl get pods -A then kubectl describe pod <name> to see network/firewall issues.

kind/kubectl not found
Re-check Phase 1 install steps.

Cleanup
bash
Copy code
kind delete cluster --name onramp
Check your understanding
Pre

Multiple choice — What does a Kubernetes Job do?
A) Runs a web server forever
B) Runs a one-off task to completion
C) Manages node upgrades
D) Stores container images

Post

True/False — After a Job completes, you can read its logs with kubectl logs job/<name>.

<details> <summary>Answer key</summary>
Pre: B
Post: True

</details> ```