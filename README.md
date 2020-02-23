# Picoquark
The simplest file system you have ever seen, literally.

## Description
No superblock, no complication. Each "file" is FIXED at 510 bytes. After that there is a 2-byte footer composed of the file type and the "name"(a byte).

The boot sector is actually a special file, with a type of system (0x55) and "name" of boot sector (0xAA).

## List of currently defined file types

### Filesystem defined
0x00 - Free sector, name doesn't matter
0x01 to 0x1E - Bad sector, name is number of sectors to skip
0x1F - Reserved for expansion
### OS defined
0x20 to 0x2F - Text file
0x30 to 0x37 - Executable
0x38 to 0x3F - Library
0x40 to 0x47 - Data file
0x48 to 0x4F - Source file
0x50 to 0x57 - Configuration file
0x58 to 0x5F - Reserved for expansion
### User defined
0x60 to 0xFE - User defined
### Filesystem defined
0xFF - End-of-medium
