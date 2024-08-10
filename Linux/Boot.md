# BIOS Files (when using GRUB)
- `boot.img` located in first 440 bytes of MBR
- `core.img` between bootstrap and first partition
- `/boot/grub/i386-pc/normal.mod` loads grub menu and reads:
- `/boot/grub/grub.cfg` display all linux kernels avaliable to load

# UEFI Files
- `grubx64/efi` located in EFI partition or `/boot`
- `/boot/grub/i386-pc/normal.mod` loads grub menu and reads:
- `/boot/grub/grub.cfg` display all linux kernels avaliable to load


## Boot and Drive Editing

- `lsblk` list blocks
- `xxd` gives a hexdump of the drive, I.E: `sudo xxd -l 512 -g 1 /dev/vda` gets a hexdump of the first 512 Bytes of /dev/vda 
- `dd` copy or write drive information

## Modules
- `ltrace -S lsmod` get all imported modules






Linux Boot Bits and Bytes 4
Execute : sudo cat /dev/vda | xxd -l 32 -c 0x10 -g 1

What are the values contained in hex positions 0x00000001 through 0x00000008?

Flag format: Value,Value,Value,...

Machine: For this challenge: Minas_Tirith (ssh from Admin_Station)
63, 90, 8e, d0, 31, e4, 8e, d8



Linux Boot MBR3
The file /home/bombadil/mbroken is a copy of an MBR from another machine.

Hash the first partition of the file using md5sum. The flag is the hash.
dd bs=1 skip==446 count=16 if=mbroken of=linuxsucks
md5sum linuxsucks
2a5948fad4ec68170b23faaa2a16cef8


Linux Boot MBR4
The file /home/bombadil/mbroken is a copy of an MBR from another machine.

You will find the "word" GRUB in the output, hash using md5sum.

The flag is the entire hash.
dd bs=1 skip=392 count=4 if=mmbroken of=linuxsucks
md5sum linuxsucks
5fa690cb0f0789cbc57decfd096a503e
