# Summary
This repo contains documentation of a project with the goal to create an ARM based home kubernetes cluster.

# Inspiration
The inspiration for this project is the [Kubernetes The Hard Way](https://github.com/kelseyhightower/kubernetes-the-hard-way) project.

# Why?
For production design decisions the 'why' is very important. For certain decisions I will try to provide a reasonable 'why', however, given this is a side project, the answer for most design decisions will be: learning/fun/curiosity.

# Contents

1. [Hardware](Hardware.md)
2. Linux Distro - Gentoo
   1. Custom Gentoo Packages
3. Networking
   1. GPGAgent
   3. IPV6
4. [Configuration Management](ConfigurationManagement.md)
   1. [LibElektra](LibElektra.md)
   2. [Puppet](Puppet.md)
   3. CFEngine
      1. Hardware Clock
      2. OpenRC Scripts
      3. Custom Promises - Package Management
5. Kubernetes
   1. Certificate Authority
   2. Etcd
6. Misc
   1. Interesting Findings
   2. Linux ACLs

