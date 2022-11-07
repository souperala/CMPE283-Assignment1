# CMPE 283 - Virtualization Technologies

## Assignment I - Discovering VMM Capabilities (Student ID: 016114254)

1. Create a virtual machine (VM) on Google Cloud Engine by following the instructions and enable the virtualization.
    - generate an ssh key on your desktop if it does not exists.
      ```
      ssh-keygen -t ed25519
      ```
    - Generate an equivalent shell command by configuring the VM with all the necessary configuration, and add extra details to the command to launch the instance.
    
    - Final cloud shell command with all the VM capabilities, ssh key and metadata.

    ![image](https://user-images.githubusercontent.com/98585812/200266041-3906ee69-bcc6-4f6b-a82c-bb49185153e7.png)
   
    <img width="924" alt="image" src="https://user-images.githubusercontent.com/98585812/200255036-3b0269a0-0222-4b02-b7de-a91fc8ae54f3.png">

    <img width="950" alt="image" src="https://user-images.githubusercontent.com/98585812/200255181-5e2116d2-8636-403e-a04e-8886746834ab.png">

     
2. Launch instance with the SSH Keys and Metadata added.

3. Login to the VM using below two methods
     - using ssh connect from the google compute engine url: https://console.cloud.google.com/compute/instances?authuser=1&cloudshell=true&project=cmpe-283-assignment1
     <img width="793" alt="image" src="https://user-images.githubusercontent.com/98585812/200257349-9b1e8f6e-14b1-4984-9c2b-1d42eeae8e53.png">
    
     - connect via ssh to the instance containing the private key for the newly added public key for your users.
4. Install all the necessary updates & dependencies using the below commands
      ```
      sudo apt-get update
      sudo apt-get upgrade
      sudo apt-get install vim gcc make linux-headers-$(uname -r)
      ```
      <img width="694" alt="image" src="https://user-images.githubusercontent.com/98585812/200258449-dca6c346-c464-47d8-8b59-3b231cbfeba0.png">
      
      <img width="468" alt="image" src="https://user-images.githubusercontent.com/98585812/200258523-4ffbaa1b-97f4-410d-875a-1e9ecc920455.png">


5. Get the Description for the specified MSRs with Addresses from the Following Pages in the Intel SDM module.
      -  IA32_VMX_PINBASED_CTLS 0x481 : Intel SDM volume 3, section 24.6.1 Table 24.5 Page 3746
      -  IA32_VMX_PROCBASED_CTLS 0x482 : Intel SDM volume 3, section 24.6.2 Table 24.6 Page 3746,3747
      -  IA32_VMX_PROCBASED_CTLS2 0x48B : Intel SDM volume 3, section 24.6.2 Table 24.7 Page 3748
      -  IA32_VMX_EXIT_CTLS 0x483 : Intel SDM volume 3, section 24.6.2 Table 24.13 Page 3756
      -  IA32_VMX_ENTRY_CTLS 0x484 : Intel SDM volume 3, section 24.6.2 Table 24.15 Page 3758
      -  IA32_VMX_PROCBASED_CTLS3 0x492 : Intel SDM volume 3, section 24.6.2 Table 24.8 Page 3749
6. define the functions for all the MSRs and code the instructions into cmpe283-1.c, copy the code and Makefile into VM using the scp command
      - create a folder cmpe283-assignment1
      - copy the files cmpe283-1.c & Makefile to the folder created
7. run the command "make" to generate the module files. 

      <img width="699" alt="image" src="https://user-images.githubusercontent.com/98585812/200261235-01538556-6b68-48d1-8c5f-77aa2c1816ed.png">

8. Insert the generated module using the "insmod" command and check the output using "dmesg".
      ```
      sudo insmod ./cmpe283-1.ko
      sudo dmesg
      ```
      <img width="468" alt="image" src="https://user-images.githubusercontent.com/98585812/200262351-fd0a137f-2476-4f83-8542-67855d000fdf.png">
      
      <img width="468" alt="image" src="https://user-images.githubusercontent.com/98585812/200262411-f5e5ada4-2e7f-4e38-bbb2-439132ef0787.png">     

      <img width="468" alt="image" src="https://user-images.githubusercontent.com/98585812/200262463-97a55d94-e400-4045-87ab-3da6d6efad37.png">    
      
      <img width="468" alt="image" src="https://user-images.githubusercontent.com/98585812/200262514-f01c439e-e52d-49c8-bac1-97c6db80d225.png">


9. Remove the generated module using the following command
      ```
      sudo rmmod cmpe283-1
      ```
### References

      - [Intel® 64 and IA-32 Architectures Software Developer Manuals](https://cdrdv2.intel.com/v1/dl/getContent/671200)
      - [Enabling nested virtualization](https://cloud.google.com/compute/docs/instances/nested-virtualization/enabling#gcloud)



