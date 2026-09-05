# Digital Forensics Lab – Data Carving & File Recovery

Module 7 lab from my Digital Forensics track (ICDFA Fellowship). Focus is on recovering
files and data when file-system metadata can't be trusted — using raw content
analysis, file signatures, and carving instead.

## What this covers

- Identifying JPEG headers/footers (SOI/EOI) with `xxd`
- Rebuilding a JPEG from a hex dump and verifying it against the original with
  MD5/SHA-256
- Pulling metadata-style strings out of a JPEG with `strings`
- Inode, block and sector-level analysis using The Sleuth Kit
  (`img_stat`, `mmls`, `fsstat`, `fls`, `icat`, `blkcat`)
- Finding embedded file structures with Binwalk
- Extracting and examining a USB forensic image, confirming partition offset
  with `mmls` rather than assuming it
- Carving deleted JPEGs off the USB image with Scalpel, and validating what
  came back

## Evidence used

- `Ch01InChap01.dd` – forensic DD image
- `J_ub_law.jpg` – JPEG for hex/signature analysis
- `120M.7z` – USB image for Scalpel carving

All evidence is training material provided for the course. Original files were
left untouched throughout — all work was done on copies in a separate working
directory.

## Repo structure

```
/evidence          original downloaded evidence + hashes
/working            copies used for analysis (nothing here touches originals)
/output
  /hex-analysis      xxd dumps, reconstructed JPEG, hash comparison
  /tsk               Sleuth Kit output (mmls, fls, fsstat, etc.)
  /binwalk           binwalk results
  /scalpel           scalpel.conf, audit.txt, carved files
/report.pdf          full write-up: commands, screenshots, findings, limitations
```

## Notes

- Where the lab guide gave a placeholder value (e.g. partition offset), I
  confirmed it against my own `mmls` output rather than copying it.
- Anything I couldn't find or verify is marked "not found" or documented as a
  limitation in the report rather than guessed at.
- No instructor-provided `File_carving.docx` was available for Part D, so
  Binwalk practice was done against the other supplied evidence instead —
  noted in the report.

See `report.pdf` for the full walkthrough with commands and screenshots.
