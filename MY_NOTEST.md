# My Notes

## SSH in GCP Compute Instance

It is simpler to manually add the public SSH key in your project metadata after generating it with __ssh-keygen__

## enable root access

In each machine run...

```bash
# First
sudo nano /etc/ssh/sshd_config
# Replace (or uncomment)  PermitRootLogin no for PermitRootLogin yes
sudo systemctl restart sshd

# Then
sudo mkdir -p /root/.ssh
sudo cp ~/.ssh/authorized_keys /root/.ssh/
sudo chown -R root:root /root/.ssh
```

## GCP VPC firewall rules

After bootrstrapping the control plane, a firewall rule enabling traffic through port 6443 must be created in the network where the VMs are set up with

## Node's hostname

After restarting the VMs, GCP might update the hostname value which could cause the kubelet to not have access to the server. 

```bash
# check node's hostname
hostnamectl status
# if you see that there is static hostname and transient hostname you must run
hostnamectl set-hostname <hostname>
```
Keep in mind that for this workshop the nodes' hostnames must be `node-0` and `node-1`
