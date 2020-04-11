# PiHole-on-K3s
An implementation of [PiHole project](https://pi-hole.net/) running on Ranchers [K3s](https://k3s.io/).

# Limitations

This setup is working for a multi-node cluster only, because PiHole is using 'low ports' for DNS and DHCP (No. 53/67), you will need a loadbalancer (MetalLB or K3s' LB) to route traffic to your pods.
Having the services run on Nodeports/Hostport did not work out for me.

# Install K3s on Raspberry

For the K3s setup part, i had great success with (Alex Ellis')[https://blog.alexellis.io/test-drive-k3s-on-raspberry-pi/] description.

# Install PiHole Image to your cluster

The YAML Definition holds Service and Deployment definition for PiHole. You need to configure following things:

1. within the Deployment.template.PodSpec section, to whatever DNS Servers you like to use. DO NOTE DELETE the localhost reference!
2. the same applies to the environment variable section at the bottom - add your DNS servers for variables DNS1 and DNS2. These are required by PiHole
3. Set a nicer Webpassword, that will be applied to the Dashboard
4. Set your ServerIP to whatever is your Node's Outbound IP Address. 

# Resource Consumption on Raspberry Pi 3

[PiHole states](https://docs.pi-hole.net/main/prerequesites/), a single instance of PiHole has hardware requirements of about 500MB system memory.
Slightly afraid if RPi3 would handle it, I noticed the memory usage is not going far over 200MB. Including K3s and containerd overhead, i am running at about 580MB (shortly over 50%) system memory usage.


