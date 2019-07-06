To debug:
1. Must have openocd open -> "sudo openocd -f interface/stlink-v2-1.cfg -f target/stm32f4x.cfg" in a seperate terminal
2. Build a .elf file and load onto target
3. Start gdb to debug -> "gdb-multiarch build/hello_world.elf" or "arm-eabi-gdb"as I have built this from source with
correct packages, so now works.
4. "target remote localhost:3333"
5. Example command "monitor reset halt"
**Must connect to the telnet ports too -- look at email for this info**

From this starting point, can now make any medium size project.
Investigate the best way to create a proper debug setup.

To allow USB access:
Go to - sudo vi /etc/udev/rules.d/"your rule".rules
for stlinkv2-1 the name is "49-stlinkv2-1.rules"

In this file write - "SSUBSYSTEMS=="usb", ATTRS{idVendor}=="0483", ATTRS{idProduct}=="374b", \
    MODE:="0666", \
SYMLINK+="stlinkv2-1_%n" **All on one line**  
