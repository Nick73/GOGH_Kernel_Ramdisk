# GOGH_Kernel_Ramdisk
**The extracted RAMDISK for GOGHVMU. Used for compiling kernels.**

The boot.img has been extracted and set up using the following commands:

        abootimg -x boot.img
        mkdir initrd && cd initrd && zcat ../initrd.img | cpio -i
        find . | cpio -o -H newc | gzip > ../initrd.img
        
To compile your own kernel, just build the zImage and replace the zImage in this repo with your own and do the following command:

        cd ../ && abootimg --create boot.img -k zImage -r initrd.img && abootimg --create boot.img -f bootimg.cfg -k zImage -r initrd.img
        
This will replace the boot.img with your new one. It should be ~5.6 MB. The full guide can be found here:

<http://www.vmroms.com/index.php?topic=919.0>

The boot.img and all folders and files in this repo are from [King Kernel] (https://github.com/Nick73/King_Kernel). The splash image during boot will show the King Kernel logo, unless the *initlogo.rle* file is changed.