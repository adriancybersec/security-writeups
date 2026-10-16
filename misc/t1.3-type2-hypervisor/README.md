# T1.3

Wednesday, 25 Feb 2026

*Originally published on my UNSW OpenLearning blog.*

## [T1.3 Hands-on Exercise: Setting up a Type 2 Hypervisor](https://www.openlearning.com/unswcourses/courses/cloud-security-comp3446-26t1/activities/t1_3_hypervisor/?cl=1)

What is the size of RAM in your physical PC?

Ram size is 16384MB = 16 GB

- How much RAM is left after you created the VM?

  12288 as the base memory takes 4096 MB = 12gb (allocated 4gb)

- Without taking advantage of any memory optimisation techniques, what is the maximum number of virtual machines you can host on your physical PC?

  Without doing the rule of thumb of leaving 4GB, 16 / 2 = 8 machines with 2gb each.

- Above, you the default value for hard disk file type (VDI). What is the difference between VDI, VHD, and VMDK?

  They are all different virtual disk file formats for different platforms.

  VDI (Virtualbox disk image) - Used for oracle virtual box

  VHD (Virtual hard disk) used for hypervisors (microsoft hyper v)

  Vmds is for VMware.

- Will the memory be applied once you power-on the VM? Why?

  Yes the memory I assign will be applied when I turn on the VM. This is done through the VM's way of dynamically allocating memory. When the VM is turned out, memory is released back into the main computer.

- Does the new memory configuration affect your physical PC (host system)? How?

  Yes but only temporarily when the VM is running, as it needs to allocate the configured amount to the VM, removing it from the actual physical PC. However once turned off it will be released back for the main pc to use.

- Change the VM network card to “Internal network”. Will the VM be connected to the Internet? (Hint: open the VM and then open www.google.com on Firefox browser to).

  No it wouldn't as it's only designed for communication if the virtual machines are on the same host and are using the same internal network name. Through my case, the VM isn't using my wi-fi, meaning it cannot send any network traffic. This is due to the VM's isolation, it can only see other virtual machines on the internal network and not on the external network.

However it's possible for the VM to connect to the internet through NAT, a network technique that allows the VM to connect into the public IP address, aka access to the internet.

Overall, i had great fun setting the VM up. It was a lengthy but fun process.
