Install DC/OS with GUI
===

In this document, we will walk you through a basic installation of DC/OS.

# Prerequisites

Minimal requirement

A custom network
```
gcloud compute networks create dcos --mode custom

gcloud compute networks subnets create dcos \
--network dcos \
--range 10.241.0.0/24 \
--region us-central1
```

```
gcloud compute firewall-rules create internal \
--allow icmp,udp,tcp \
--network dcos
--source-ranges 10.240.0.0/24

gcloud compute firewall-rules create bootstrap \
--allow icmp,tcp:80,tcp:443,tcp:8080,tcp:8181,tcp:2181,tcp:5050
--network dcos
--source-ranges 0.0.0.0/0

```

Create instances
```
gcloud compute instances create 

gcloud compute instances list

```

Docker 
```
sudo yum install -y docker-engine-1.13.1 docker-engine-selinux-1.13.1
sudo systemctl start docker
sudo systemctl enable docker
```

# Install bootstrap node

```
curl -O https://downloads.dcos.io/dcos/stable/dcos_generate_config.sh
sudo bash dcos_generate_config.sh --web
```

```
====> Starting DC/OS installer in web mode
DC/OS Installer
Using selector: EpollSelector
Starting server ('0.0.0.0', 9000)
```

GO to http://<bootstrap-public-ip>:9000


