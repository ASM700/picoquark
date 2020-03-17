# Picoquark v1.1

This is an *updated* version of PicoQuark.

## Description

No superblock, no complication. Each "file" is a multiple of 510 bytes. After each 510-byte "block" there is a 4-byte footer composed of:
  - The next file "name" (0x0000 if free)
  - File type (byte)
  - File type (name)

The boot sector is actually a special file, with a type of system (0x55) and "name" of boot sector (0xAA).

## List of currently defined file types

| Type      | Name                      | Usage         |
|-----------|---------------------------|---------------|
| 0x00      | Doesn't matter            | Free Sector   |
| 0x01-0x1E | Number of sectors to skip | Bad Sector(s) |
| 0x1F      | Doesn't matter            | Reserved      |

| Type      | Name      | Usage         |
|-----------|-----------|---------------|
| 0x20-0x2F | 0x00-0xFF | Text/Log file |
| 0x30-0x3F | 0x00-0xFF | Executable    |
| 0x40-0x47 | 0x00-0xFF | Data file     |
| 0x48-0x4F | 0x00-0xFF | Source file   |
| 0x50-0x54 | 0x00-0xFF | Bitmap        |
| 0x55      | 0x00-0xA9 | Bitmap        |
| 0x55      | 0xAA      | Bootsector    |
| 0x55      | 0xAB-0xFF | Bitmap        |
| 0x56-0x5F | 0x00-0xFF | Raw binary    |
| 0x60-0x62 | 0x00-0xFF | Disk Image    |
| 0x63      | 0x00-0xFF | Floppy Image  |
| 0x64-0x67 | 0x00-0xFF | HTML/XHTML    |
| 0x68-0x6A | 0x00-0xFF | CSS/SASS      |
| 0x6B-0x6E | 0x00-0xFF | JS            |
| 0x6F      | 0x00-0xFF | JSON          |
| 0x70-0x71 | 0x00-0xFF | OBJ (3D)      |
| 0x72-0x73 | 0x00-0xFF | BLEND (3D)    |
| 0x74-0x7F | 0x00-0xFF | MP4           |
| 0x80-0xFD | 0x00-0xFF | User-defined  |
| 0xFE      | 0x00-0xFF | ID            |
| 0xFF      | 0x00-0xFF | End of medium |
