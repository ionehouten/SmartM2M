# SMARTM2M TEST
## Case Study 2 : Kubernetes


```bash
# Deploy nginx app
kubectl apply -f deployment.yaml

# Update nginx new version 1.11.13-alpine
kubectl annotate deployment nginx-app -n default kubernetes.io/change-cause="update image to nginx:1.11.13-alpine" --overwrite=true
kubectl set image deployment/nginx-app -n default app=nginx:1.11.13-alpine 

# Show history deployment
kubectl rollout history deployment -n default nginx-app

# Rollback that update to the previous version 1.11.10-alpine
kubectl rollout undo deployment -n default nginx-app

# Rollback with specific revision
kubectl rollout undo deployment -n default nginx-app --to-revision={{ specific_revision }}

# Set node k8s-node-1 as unavailable and reschedule all the pods running on it
kubectl drain --ignore-daemonsets --delete-emptydir-data k8s-node-1


# Create PersistentVolume and PersistentVolumeClaim
kubectl apply -f pvc.yaml

# Worker Node Joins
kubeadm join {{ ip }}:6443 --token={{ token }} --discovery-token-ca-cert-hash  {{discoverytoken}}
```
