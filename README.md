# PiHole-on-K3s
An implementation of [PiHole project](https://pi-hole.net/) running on Ranchers [K3s](https://k3s.io/).

# Resource Consumption on Raspberry Pi 3

[PiHole states](https://docs.pi-hole.net/main/prerequesites/), a single instance of PiHole has hardware requirements of about 500MB system memory.
Slightly afraid if RPi3 would handle it, I noticed the memory usage is not going far over 200MB. Including K3s and containerd overhead, i am running at about 580MB (shortly over 50%) system memory usage.


