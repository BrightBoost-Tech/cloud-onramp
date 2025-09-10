# Cloud On-Ramp (Zero → VM → GPU → K8s Job)
Requirements: cloud account (for VM/GPU), Docker+kind+kubectl, SSH key.

1) First VM (10–20 min)
   - Create smallest Linux VM; open SSH (22) to your IP
   - ssh -i KEY.pem user@IP
   - Run hello Python script → Verify “hello, cloud”

2) First GPU Job (15–30 min)
   - Create smallest GPU VM; `nvidia-smi`
   - Run tiny PyTorch check → Verify CUDA True/False

3) First K8s Job (10–20 min)
   - `kind create cluster --name onramp`
   - `kubectl apply -f hello-job.yaml`
   - `kubectl logs job/hello-job` → Verify message

Stop/terminate VMs when finished • Repo: <repo URL>
