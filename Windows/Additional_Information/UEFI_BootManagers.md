UEFI Boot Manager: Unlike the BIOS (that reads the MBR), the UEFI reads an EFI Partition.
        - The EFI Partition contains UEFI Boot Managers [Windows bootmgfw.efi or Windows Boot Manager]

### bootmgfw.efi(UEFI) reads a BCD(Boot Configuration Data) in the EFI system partition to load the winload.efi file
