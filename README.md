# 283-assignment2
## Team Members:
### Jinxuan Hu(013728936)
### Xuan Shi ()

## Contribution :
### Jinxuan Hu --- Build the kernel, modify the file vmx.c, compile the test file  and create the documentation. 
### Xuan Shi ---- Build the kernel, modify the file cpuid.c, create the test file and update the documentation.

## Steps:
### Build the kernel for the first time

1. Clone  the linux repository by using the following command:                                                                                           
	` $git clone https://github.com/torvalds/linux.git`
2. Install all the necessary packages required to compile by using this command:                                                                         
	`$ sudo bash`                                               
	`$ apt-get install build-essential kernel-package fakeroot libncurses5-dev libssl-dev ccache bison flex libelf-dev` 
3. Check the current kernel verssion by using this command:  
	 `$ uname -a`  
	  the kernel version is "5.8.0-50-generic".
4. Build the kernel for the first time by using the following commands:         
	* 	`$ cp /boot/config-5.8.0-50-generic    ./.config `  
	* 	`$ make oldconfig` (just use the default for everything)   
	* 	`$ make -j 2` 
	*  `$ sudo make -j 2 modules`
	* 	`$ sudo make install`
	* 	`$ sudo make modules-install`
	* 	`$ reboot`	
5. After the initial build, verify that the newest version kernel can be used after rebooting:  
	`uname -a `.  
	current kernel version is 5.12.0

### Modify the CPUID emulation code
1. Modify the CPUID emulation code in KVM by modifing the following two files. 
*  In cpuid.c, we created a new cpuid leaf in the function `kvm_emulate_cpuid`,which is to test the number of exits while eax == 0x4FFFFFFF   .[]()
*  In vmx.c, we defined two global variables: `num_of_ exist` and `cpu_cycles` to calculate the number of exits and processing time of each exit. In addition, the `vmx_handle_exit` function can be used to calculate the number of exits and total time spend processing all exits.
2. After modfing the files, rebuild the kernel by using the command for initial build.   
3. Reboot VM by using command:  
`$ reboot`

### Inatall nested VM 
1. Install the nested VM with the following guild:
	https://phoenixnap.com/kb/ubuntu-install-kvm#ftoc-heading-5
2. Install essential KVM packages with the following command:
	`sudo apt install qemu-kvm libvirt-daemon-system libvirt-clients bridge-utils`.
3.  Check the status of libvirtd:
	`sudo systemctl status libvirtd`
	 the output returns an active (running) status.
4.  Install virt-manager by using the following command:
  	`sudo apt install virt-manager`
5.  Start virt-manager by using the following command:
	`sudo virt-manager`
6.  Download Ubuntu20.04 and install it.
7.  Open the inner VM terminal and install cpuid by using:
	* `sudo apt-get update `
	* `sudo apt-get install cpuid`

## Test and output
1. Create test file and test which is to calculate the number of exits and processing time of the exits.
2. Compile the testfile 
	`sudo apt-get install make`
	`sudo apt-get install gcc`
	`gcc test.c -o test`
	`./test`
3. Output:





