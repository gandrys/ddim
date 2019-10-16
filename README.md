
# *ddim [Andrys Jiri, 2019.10.16, v0.03 ]*  

 Author        : Jiri Andrys  
 Maintainer    : Jiri Andrys  
 Contributors  : Jiri Andrys  
  
# 1. Contents:

* [2. Overview](#2-overview)
* [3. Installation](#3-installation)
* [4. Run](#4-run)
* [5. Dependency List](#5-dependency-list)
* [6. Examples](#5-examples)

# 2. Overview
The `ddim` copy data to SD-CARD image. Only MBR/DOS is supported. 
Resize partitions if necessary. Resizig FATXX filesystems in not supported.

The `ddim` has been tested on following systems:  

  * Ubuntu 16.04(64bit, docker image )   

# 3. Installation

- **No installation is necessary.** 


## 4. Run

Tool asks for necessary information, no need to fill any parameters, if necessary call commmand with  --help parameter.  

>`$ ddim`  

For more information.:
>`$ ddim --help`  


# 5. Dependency List

1. Standard tools, included in almost all kind of distros and installed by default:  
   >` bash, "date, parted, awk, dd, cp, rm, kpartx, e2fsck, resize2fs, mkfs.extX, 
   mkfifo, losetup, du, tar, df, mount/umount,  rmdir `  

   
# 5. Examples 

### 5.1.1. Copy directory "bla" to partition 2 of SD-CARD image : 

User does not need to know any parameter, tool will ask for any necessary information.
Note: "bla" directory includes one file bla.pdf(bla/bla.pdf)

```bash
1. $ fslbsp$ ddim  

Enter path to raw-image file(*.sdcard) or tar archive with raw-image(*.tar.xz)
>my-board-dev-image-base-imx6dl-20191016094434.rootfs.sdcard

Select partition number[1-4]:

    Partition		 Start		 End		 Size		 FS
	1		4194kB		12.6MB		8389kB					
	2		12.6MB		2525MB		2512MB		ext4			
	3		2525MB		4672MB		2147MB		ext4			
>2

Enter destination directory on sd-card: 
>/test/test2

Enter tar archive or some directory to copy on sd-card: 
>bla/

Check available space, mount:
>OK

Check available space, umount:
>OK

Mount:

Copy data to raw image:

Umount:

>OK

```   

### 5.1.2. Mount partition 2 of SD-CARD image and manually remove files from previous step : 

In first terminal window we run ddim tool:  

```bash
1. $ fslbsp$ ddim -m 

Enter path to raw-image file(*.sdcard) or tar archive with raw-image(*.tar.xz)
>my-board-dev-image-base-imx6dl-20191016094434.rootfs.sdcard

Select partition number[1-4]:

    Partition		 Start		 End		 Size		 FS
	1		4194kB		12.6MB		8389kB					
	2		12.6MB		2525MB		2512MB		ext4			
	3		2525MB		4672MB		2147MB		ext4			
>2

Partition 2 is mounted to: /tmp/tmp.ateHQ3vssE

Press enter to umount:
  >

```   

In second terminal window we remove files, step by step, just for demonstration:  

```bash
1. $ fslbsp$ cd /tmp/tmp.ateHQ3vssE
2. $ /tmp/tmp.ateHQ3vssE$ sudo rm test/test2/bla.pdf
3. $ /tmp/tmp.ateHQ3vssE$ sudo rm -rf test
``` 
