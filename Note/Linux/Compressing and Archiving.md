
#### Compression

- **Compression** reduces file size by encoding data more efficiently, saving storage and speeding transfers.
- Two types:
 **Lossless:** No data loss; used for text, executables. Tools: `gzip`, `bzip2`, `xz`.
 **Lossy:** Some data loss for smaller size; used for media files (images, audio, video).
- Various tools/formats offer different compression ratios, speed, and resource use

#### Archiving

- **Archiving** bundles multiple files/directories into a single file (**archive**) preserving structure, permissions, and metadata.
- Common tool: `tar` (Tape Archive).
- Archiving itself doesn’t compress files but can be combined with compression (`gzip`, `bzip2`, `xz`).
- Purpose of archiving
- Organize multiple files into one file
- Backup and restore data easily
- Facilitate efficient data transfer
- Preserve file attributes (permissions, timestamps)
- Software distribution (e.g., `.tar.gz`)
- Long-term storage

#### Tarring Files

- Use `tar` to create an archive (tarball) without compression:
    ```bash
  tar -cvf archive.tar folder1 file1.txt
    ```

- `c`: create archive
- `v`: verbose (show progress)
- `f`: specify archive file name
![[Pasted image 20250815120823.png]]

#### Compressing Archives

- Compress tar archives to reduce size:
- **gzip:** `.tar.gz` or `.tgz` (fast, moderate compression)
```bash
  gzip archive.tar
  ```
![[Pasted image 20250815120851.png]]



- **bzip2:** `.tar.bz2` (better compression, slower)

```bash
bzip2 archive.tar
bzip2 archive.tar.gz
  ```
  
  ![[Pasted image 20250815120935.png]]
  
- we can also compress individual files directly:
```bash
 gzip file1.txt file2.txt
```


#### Untarring (Extracting Archives)

- Extract files from a tar archive:
```bash
tar -xvf archive.tar
 ```

- `x`: extract
- `v`: verbose
- `f`: archive file name

![[Pasted image 20250815121223.png]]

#### Decompression

- Restore compressed files to original state:
- For gzip files:

```bash
  gunzip file.txt.gz
  ```

![[Pasted image 20250815121324.png]]

- For bzip2 files:
```bash
bunzip2 file.txt.bz2
```

![[Pasted image 20250815121353.png]]
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



![[Pasted image 20260317200027.png]]
