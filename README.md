# ICDFA Ch02 Forensics Lab - Data Carving and Raw File Recovery

## Overview
This lab is a practical digital forensics investigation conducted as part of the ICDFA Fellowship in Web Application Security and Digital Forensics. The objective was to examine raw file content, identify file signatures, recover embedded content, and carve deleted files from a USB forensic image.

## Investigator
- **Name:** Adeleye Ademiluyi Timilehin
- **Institution:** International Cybersecurity and Digital Forensics Academy (ICDFA)
- **Batch:** B2025
- **Registration:** 2025/FWSD/11459

## Evidence Files
- **Ch01InChap01.dd** — 1.5MB — Forensic DD Image
- **J_ub_law.jpg** — 1.7MB — JPEG Sample for Hex and Signature Analysis
- **120M.7z** — 36MB — USB Image for Scalpel File Carving (usb_fat_carving.001 — 119MB)

## Evidence Hashes
| File | MD5 | SHA-256 |
|---|---|---|
| Ch01InChap01.dd | a117773bcf1fc88ec0ab8e0a349fbbcb | 3ce8053e4f3d9c8ab98b3aadb2480685efb8e4980d34297b83bd5a09b1a7b122 |
| J_ub_law.jpg | 83a360ac7f7e0ca318e5bfe39f95f137 | 238ff34393c50e52c0e8b14fcff8ec7dc29e23914dbc435f8ef998d172a91468 |
| 120M.7z | dfe7b5424e54cd1bf50d5df47aceeb3c | 2d2a3d93c9ec65bcad9f89c9894429ea72caa8add07726a3b96ec9a6ab6a58ce |
| usb_fat_carving.001 | ba4a1d0ba49f4a6667b00a3b3e85e604 | Verified by FTK Imager |

## Tools Used
- **xxd** - Hex dump and file signature analysis
- **strings** - Metadata extraction from binary files
- **Binwalk** - Embedded file discovery
- **Autopsy 2.24** - GUI forensic analysis
- **Sleuth Kit** - img_stat, mmls, fsstat, fls, istat, icat, blkcat
- **7zip** - Archive extraction
- **Scalpel** - File carving (Part F)
- **md5sum / sha256sum** - Evidence integrity verification

## Lab Structure
- evidence/ - Original evidence files
- recovered_files/ - Files recovered from disk images
- screenshots/ - Evidence screenshots for all parts
- reports/ - Final forensic PDF report
- sleuthkit_output/ - Command line tool outputs
- carving_output/ - Scalpel carved files

## Part A - File Signatures and Hex Analysis
- JPEG header FF D8 confirmed at offset 0x00000000
- JPEG footer FF D9 confirmed at offset 0x0019d1f6
- Image reconstructed from hex dump — MD5 hash verified identical

## Part B - Metadata Analysis
- Camera: NIKON D4 (NIKON CORPORATION)
- Software: Adobe Photoshop 21.1 (Macintosh)
- Date: 2020-08-20 10:20:05
- Photographer: HOWARD KORN
- Lens: 17.0-35.0mm f/2.8

## Part C - Sleuth Kit Analysis
- File system: FAT12, offset 0
- 6 files found, 4 deleted
- INCOME.XLS recovered at inode 13, sectors 285-311

## Part D - Binwalk
- J_ub_law.jpg: JPEG + embedded TIFF thumbnail + Adobe copyright string
- Ch01InChap01.dd: No embedded files detected

## Part E - USB Image
- Partition offset: 128 (confirmed via mmls)
- File system: FAT16, volume label: USB
- 35 files found, 32 deleted across multiple file types

## Part F - Scalpel (Limitation)
- Scalpel configuration initiated, JPEG entries identified
- Full carving operation pending — to be submitted separately

## Key Findings
- INCOME.XLS successfully recovered from Ch01InChap01.dd
- Photographer HOWARD KORN identified from J_ub_law.jpg metadata
- 32 deleted files identified on USB image ready for carving
- All evidence hashes verified before and after analysis

## GitHub Repository
https://github.com/Adeleye001/ICDFA-Ch02-Forensics-Lab
