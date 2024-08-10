# BIOS Files (when using GRUB)
- `boot.img` located in first 440 bytes of MBR
- `core.img` between bootstrap and first partition
- `/boot/grub/i386-pc/normal.mod` loads grub menu and reads:
- `/boot/grub/grub.cfg` display all linux kernels avaliable to load

# UEFI Files
- `grubx64/efi` located in EFI partition or `/boot`
- `/boot/grub/i386-pc/normal.mod` loads grub menu and reads:
- `/boot/grub/grub.cfg` display all linux kernels avaliable to load


# Viewing and Copying Drives

- `lsblk` list blocks

## dd (Data Duplicator)
A command to copy binary data

### Syntax
```
dd if=<infile> of=<outfile> ibs=1 [skip=<skip-bytes>] [count=<length>]
```
- `if=` specifies the input file (a drive can be specified)
- `of=` specifies the output file (a drive can be specified)
- `ibs=` specifies the bytes to count by (for skip and count), it is recommended to set this as `1`
- `skip=` skips bytes when reading based on: (skip * ibs) = bytes to skip 
- `count` the number of bytes to read after skipping based on: (count * ibs) = bytes and then writes said bytes to the outfile

### Examples

```
dd if=/dev/sda of=outfile ibs=1 skip=512 count=16
```
This command reads the binary file `/dev/sda` it skips the first 512 bytes or goes to offset 0x200 and grabs 16 bytes of data. The program then writes the 16 bytes to the file 'outfile'

```
dd if=testmbr of=hinaryfile ibs=16 skip=4 count=1
```
This command reads the binary file `testmbr` it skips the first 64 bytes (4 * 16) or goes to offset 0x40 and grabs 16 bytes (1 * 16) of data. The program then writes the 16 bytes to the file 'binaryfile'

- `xxd` gives a hexdump of the drive, I.E: `sudo xxd -l 512 -g 1 /dev/vda` gets a hexdump of the first 512 bytes of /dev/vda 
- `dd` copy or write drive information

## Modules
- `ltrace -S lsmod` get all imported modules






Linux Boot Bits and bytes 4
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
