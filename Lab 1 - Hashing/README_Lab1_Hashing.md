# Lab 1: File Hashing and Hidden Data in JPEG Files

## Overview

This lab is part of a computer forensics portfolio that analyzes a single suspect disk image, `Vader_Home_Computer.001`. It focuses on **file hashing** as a way to verify evidence integrity and compare files, and on how **data can be hidden inside a JPEG** without changing how the picture looks.

**Tools used:** FTK Imager, HashCalc, HxD Hex Editor

**Skills demonstrated:** evidence export, MD5 hashing, hex-level file inspection, file-structure analysis (JPEG markers), documenting findings

## The Challenge

Three pictures (`me & the guys1.jpg`, `me & the guys2.jpg`, `me & the guys3.jpg`) were found in the `Secret pics` folder of the suspect's computer. They look similar, but an investigator cannot rely on appearance alone. The questions to answer were:

- Are the three pictures really identical?
- How reliable is an MD5 hash as a digital fingerprint of a file?
- Is anything suspicious hidden inside the files?

## The Solution

1. **Exported the evidence.** Loaded the image in FTK Imager and exported the folder `C:\Documents and Settings\Owner\My Documents\Secret pics` to a local drive.
2. **Compared the files.** Recorded the file size of each picture and described its contents.
3. **Hashed the files.** Calculated the MD5 hash of each file with HashCalc to find which files were truly identical.
4. **Tested hash sensitivity.** Using HxD, changed only the **last byte** of a copy of one file, saved it under a new name, and re-hashed it. The file size and the visible picture stayed the same, but the MD5 hash changed completely.
5. **Inspected the end of each file.** In HxD, checked the last bytes of every file. A normal JPEG ends with the marker `FF D9`.

## Key Findings

| Finding | Result |
|---|---|
| Effect of changing 1 byte | Completely different MD5 hash, same file size and same-looking image |
| `me & the guys1.jpg` and `me & the guys3.jpg` | End with the standard JPEG end marker `FF D9` |
| `me & the guys2.jpg` | **No `FF D9` marker.** The end of the file contains ASCII text (`DEATH_STAR_PASSWORD IS: CutePuppies123:)`) starting at offset `0003EF10` |

## Conclusion

- MD5 is very sensitive to changes, which makes it useful for verifying integrity and detecting duplicates. Because MD5 has known collision weaknesses, a stronger algorithm such as SHA-256 should be used alongside it for serious evidence.
- A JPEG can carry hidden information at its end and still open normally. Detecting this requires byte-level inspection, hash comparison, and checking the file structure, not just viewing the picture.

## Evidence and Documentation

Screenshots and the full lab report: `[LINK]`

## Repository Structure

```
Lab1-Hashing/
├── README.md
├── report/        # lab report (DOCX/PDF)
└── screenshots/   # FTK Imager, HashCalc, HxD evidence
```
