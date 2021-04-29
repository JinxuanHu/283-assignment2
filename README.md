# 283-assignment2
## Team Members:
### Jinxuan Hu(013728936)
### Xuan Shi ()

## Contribution 
### Jinxuan Hu --- Build the kernel, modify the file vmx.c and create the documentation. 
### Xuan Shi ---- Build the kernel, modify the file cpuid.c and create the test file. 

## Steps
### Build the kernel for the first time

1. Clone  the linux repository by using the following command: .
	` $git clone https://github.com/torvalds/linux.git`
2. Install all the necessary packages required to compile by using this command:
	`$ apt-get install build-essential kernel-package fakeroot libncurses5-dev libssl-dev ccache bison flex libelf-dev` 
3. Check the current kernel verssion by using this command(the kernel version is "5.8.0-50-generic"):  
	 `$ uname -a`
4. Build the kernel for the first time by using the following commands:         
	`$ cp /boot/config-5.8.0-50-generic    ./.config `  
	`$ make oldconfig` (just use the default for everything).   
	`$ make -j 2 && make -j 2 modules && make install && make modules-install` (2 is the number of cpus in my vm)  
	`$ reboot`
	
5. After the first build, verify that the newest version kernel can be used after rebooting:  
	`uname -a `.  
	kernel version is 5.12.0

### Modify the CPUID emulation code
1. Modify the CPUID emulation code in KVM by modifing the following two files. 
*  In cpuid.c, we created a new cpuid leaf in the function `kvm_emulate_cpuid`.  
*  In vmx.c, we defined two global variables: `no_of_ exist` and `cpu_cycles` to calculate the number of exits and processing time of each exit. In addition, the `vmx_handle_exit` function can be used to calculate the number of exits and total time spend processing all exits.
2. After modfing the files, rebuild the kernel by using the following command:   
`$ sudo make -j modules M=arch/kvm/x86` 
3. Reboot VM by using command:  
`$ reboot`

### Inatall nested VM 
1.

## Test and output
1. 


