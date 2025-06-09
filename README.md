# linux-2.4

- link: https://mirrors.edge.kernel.org/pub/linux/kernel/v2.4/linux-2.4.0.tar.xz

- root:
    - http://cdimage.debian.org/mirror/cdimage/archive/older-contrib/2.2/debian-2.2r0-i386-CD1.iso
    - install/root.bin -> gzip -dc root.bin > hda.img
    - cann't config devfs, would remount dev so that not find device node.

- exec:
    - make menuconfig
    - make vmlinux -j8
    - make bzdisk
    - qemu-system-i386 -m 4G -boot a -serial stdio -blockdev driver=file,node-name=f0,filename=floppy.img -device floppy,drive=f0 -hda hda.img
    - qemu-system-i386 -m 4G -boot a -serial stdio -fda floppy.img -hda hda.img
    - target remote 192.168.33.1:1234
