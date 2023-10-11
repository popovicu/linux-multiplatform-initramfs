# Linux multiplatform initramfs with Bazel

This repository has an example for cross-compiling a simple `initramfs` image to `ARM`, as well as compiling it for `x86_64`, using Bazel. If you're unfamiliar with Bazel, please check out [this guide](https://popovicu.com/posts/build-all-software-in-one-command-with-bazel/).

**This repo is meant to accompany the article at http://popovicu.com/posts/building-multiplatform-linux-initramfs-with-one-command-in-bazel** 

## `x86_64` image

To build, run the following:

```
bazel build --platforms=//platforms:x86_64_linux //init:initramfs
```

Build a working Linux kernel that can execute Go code (if you haven't changed the config too much, this should mean there's nothing for you to do) and run all this in QEMU:

```
qemu-system-x86_64 -kernel arch/x86/boot/bzImage -initrd PATH_TO_THIS_PROJECT/bazel-bin/init/initramfs.cpio -nographic  --append "console=ttyS0"
```

Sample output:

```
[    2.008520] Run /init as init process
Hello from init
Hello! I'm on x86_64.
```

## ARM image

To build, run the following:

```
bazel build --platforms=//platforms:arm_linux //init:initramfs
```

Similar to the above, build a working ARM Linux kernel and run in QEMU:

```
qemu-system-arm -machine virt -kernel arch/arm/boot/zImage -initrd PATH_TO_THIS_PROJECT/bazel-bin/init/initramfs.cpio -append "root=/dev/mmcblk0 console=ttyAMA0" -nographic
```

Sample output:

```
[    1.217946] Run /init as init process
Hello from init
Hey! I'm running on ARM.
```