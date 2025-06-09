# linux-2.4

- link: https://mirrors.edge.kernel.org/pub/linux/kernel/v2.4/linux-2.4.0.tar.xz

- exec:
    - make menuconfig
    - make vmlinux -j8
    - make bzdisk
    - qemu-system-i386 -m 4G -boot a -serial stdio -blockdev driver=file,node-name=f0,filename=floppy.img -device floppy,drive=f0 -hda hda.img
    - target remote 192.168.33.1:1234
