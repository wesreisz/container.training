# Pre-requirements

- Be comfortable with the UNIX command line

  - navigating directories

  - editing files

  - a little bit of bash-fu (environment variables, loops)

- Some Docker knowledge

  - `docker run`, `docker ps`, `docker build`

  - ideally, you know how to write a Dockerfile and build it
    <br/>
    (even if it's a `FROM` line and a couple of `RUN` commands)

- It's totally OK if you are not a Docker expert!

---

class: title

*Tell me and I forget.*
<br/>
*Teach me and I remember.*
<br/>
*Involve me and I learn.*

Misattributed to Benjamin Franklin

[(Probably inspired by Chinese Confucian philosopher Xunzi)](https://www.barrypopik.com/index.php/new_york_city/entry/tell_me_and_i_forget_teach_me_and_i_may_remember_involve_me_and_i_will_lear/)

---

## Hands-on sections

- The whole workshop is hands-on

- We are going to build, ship, and run containers!

- You are invited to reproduce all the demos

- All hands-on sections are clearly identified, like the gray rectangle below

.exercise[

- This is the stuff you're supposed to do!


<!-- ```open @@SLIDES@@``` -->

]

---

class: in-person

## Where are we going to run our containers?

---

class: in-person, pic

![You get a cluster](images/you-get-a-cluster.jpg)

---

class: in-person

## You get a cluster of cloud VMs

- I won't be using the same clusters that the original material covers

- You will each have your own EKS cluster (We'll talk about some of the differences)

- Kubectl is used to manage your cluster. This will be installed on your local machine (it's a single binary that will 
need to be in your path)

```bash
kubectl cluster-info
Kubernetes master is running at https://DF109763A68ED929C60134D38EA4D839.gr7.us-east-1.eks.amazonaws.com
CoreDNS is running at https://DF109763A68ED929C60134D38EA4D839.gr7.us-east-1.eks.amazonaws.com/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy
```

---

class: in-person

## Why don't we run containers locally?

- Installing this stuff can be hard on some machines

  (32 bits CPU or OS... Laptops without administrator access... etc.)

- *"The whole team downloaded all these container images from the WiFi!
  <br/>... and it went great!"* (Literally no-one ever)

- All you need is a computer (or even a phone or tablet!), with:

  - an internet connection

  - a web browser

  - an SSH client

---

class: in-person

## SSH clients

- On Linux, OS X, FreeBSD... you are probably all set

- On Windows, get one of these:

  - [putty](http://www.putty.org/)
  - Microsoft [Win32 OpenSSH](https://github.com/PowerShell/Win32-OpenSSH/wiki/Install-Win32-OpenSSH)
  - [Git BASH](https://git-for-windows.github.io/)
  - [MobaXterm](http://mobaxterm.mobatek.net/)

---

class: in-person

## Connecting to Our Environment

- We'll dive into kubectl more in a bit, but for now... let's make sure we have it installed

.exercise[
If you don't have kubectl installed, install it: (https://kubernetes.io/docs/tasks/tools/install-kubectl/)
& get validate you can get a version 'kubectl version --client'
]

Tip:
```bash
curl -LO "https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/darwin/amd64/kubectl"
chmod +x ./kubectl
sudo mv ./kubectl /usr/local/bin/kubectl
kubectl version --client
```
---

class: in-person

## Connecting to Our Environment

- Now let's get to our cluster...

.exercise[
This is the info needed to connect to the cluster
]