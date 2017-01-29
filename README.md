Shrine
======

![Screenshot](http://imgur.com/xDC3hwx.png)

Shrine is a TempleOS distribution that aims to be more modern & approachable.

Shrine aims to improve upon TempleOS in several aspects:
- Approachability: Shrine ships with Lambda Shell, a more traditional Unix-like command interpreter
- Connectivity: Snail is a tunelled network interface that lets you connect to the internet
- Software access: Shrine includes a package downloader
- Versatility: unlike stock TempleOS, Shrine requires only 64MB RAM, making it feasible for cloud micro-instances and similar setups (note: this is planned, but currently not true)

Software included in Shrine:
- Mfa (minimalist file access)
- Lsh (Lambda Shell)
- Pkg (package downloader)
- Wget

Setting up with networking
==========================
- To enable networking through Snail:
  - configure your VM: COM2 - TCP, server, 7777
  - start the VM
  - run ./snail.py
  - you will now be able to access the Internet, try for example `pkg-list`
  
- To enable file access through Mfa, configure the VM as follows:
  - configure your VM: COM1 - TCP, server, 7770
  - start `/Apps/Mfa.HC.Z` in the VM
  - on the host, use ./mfa.py to transfer commands and files
  - for example: `./mfa.py list /Apps/Mfa.HC.Z Mfa.HC`

Both of these can be used simultaneously.

Package management functions
============================

Note: In Lsh, use `pkg-install xyz` in place of `PkgInstall("xyz")` etc.

- `PkgList;`

  List all packages available in the repository.

- `PkgInstall(U8* package_name);`

  Download & install a specific package.

- `PkgInstallFromFile(U8* manifest_path);`

  Manually install a downloaded package. Manifest must reference an existing .ISO.C path.

- `PkgMakeFromDir(U8* manifest_path, U8* src_dir);`

  Build a package from directory contents. For an example manifest, check [here](Shrine/Packages/Lsh/manifest). Manifest must reference a valid .ISO.C path which will be used as **output**!

- `PkgMakeFromFile(U8* manifest_path, U8* file_path);`

  Build a package from a single file. See above for details.

Building from source
====================

(See here)[BUILDING.md]