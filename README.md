# Picoquark
The simplest file system you have ever seen, literally.

## Description
No superblock, no complication. Each "file" is FIXED at 510 bytes. After that there is a 2-byte footer composed of the file type and the "name"(a byte).

The boot sector is actually a special file, with a type of system (0x55) and "name" of boot sector (0xAA).

## List of currently defined file types

### Filesystem defined
0x00 - Free sector, name doesn't matter
0x01 to 0x1E - Bad sector, name is number of sectors to skip
0x1F - Reserved
### OS defined
0x20 to 0x2F - Text file
0x30 to 0x37 - Executable
0x38 to 0x3F - Library
0x40 to 0x47 - Data file
0x48 to 0x4F - Source file
0x50 to 0x54, 0x56 and 0x57 - Configuration file
0x55 - SYSTEM
0x58 to 0x5F - Reserved for expansion
### User defined
0x60 to 0xFE - User defined
### Filesystem defined
0xFF - End-of-medium

## How to...
### Create a file
  - Find end-of-medium marker
  - Create a second end-of-medium after the current one
  - Replace the first end-of-medium with the file
 ### Delete a file
  - Find the file by "name"
  - Replace the type with a free sector
 ### Rename a file
  - Find the file by "name"
  - Replace the footer with the updated "filename"
 ### Modify a file
  - Find the file by "name"
  - Replace the contents with the modified contents
 ### Format a medium
  - Write a program that displays a message (e.g. remove device and try again) and write the signature to the boot sector
  - Write a end-of-medium marker
 
 ## Limitations
  - Maximum of 65535 files
  - No directories
  - Annoying file size limit
 ## Cool stuff
  - Super simple and easy to implement
  - It's technically a *"real"* filesystem
  - If you lose 6 sectors, you lose 6 files, not the whole FS.
