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
