BIOS (supports up to 2 Terabytes)
   - MBR (Master Boot Record): contains Disk Partitions
        ### The MBR is 512 bytes, separated into 6 parts:
         - Bootstrap Code (446 bytes)
         - Partition entry 1 (16 bytes)
         - Partition entry 2 (16 bytes)
         - Partition entry 3 (16 bytes)
         - Partition entry 4 (16 bytes)
         - Boot Signature (2 bytes)
               - The Partition code that starts the first stage of loading an Operating System is referred to as the "Boot Loader"    
