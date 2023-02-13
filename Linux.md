
# Linux

The commands detailed in this file apply to Linux-based terminals.

## Create Symbolic Link

```shell
ln -s <original_source_file_path> <target_link_file_path>
```

## Delete Link

Delete ONLY the specified link to a file (do not delete the source file itself).

```shell
unlink <link_file_path>
```

## Find Text

Find text in files in the specified path.

```shell
grep [--include=\*.{c,h}] [--exclude=\*.o] -rnwil '<path>' -e '<pattern>'
```

_NOTE: The `--include` flag specifies the search should only include files whose paths match the \<include_pattern\>._  
_NOTE: The `--exclude` flag specifies the search should exclude any files whose paths match the \<exclude_pattern\>._  
_NOTE: The `-r`/`-R` flag specifies the search should be recursive._  
_NOTE: The `-w` flag specifies the search should match the whole word._  
_NOTE: The `-i` flag specifies the search should ignore case (be case-insensitive)._  
_NOTE: The `-n` flag specifies the search result should also return the line number(s) of the match(es)._  
_NOTE: The `-l` flag specifies the search result should show the file path--not the match result line itself._

## Find File - By Contained Text

Find files in the specified path containing text matching the specified pattern.

```shell
grep -n '<pattern>' '<path>'
```

Alternatively,

```shell
grep -rnw '<path>' -e '<pattern>'
```

_NOTE: The `--include` flag specifies the search should only include files whose paths match the \<include_pattern\>._  
_NOTE: The `--exclude` flag specifies the search should exclude any files whose paths match the \<exclude_pattern\>._  
_NOTE: The `-r`/`-R` flag specifies the search should be recursive._  
_NOTE: The `-w` flag specifies the search should match the whole word._  
_NOTE: The `-i` flag specifies the search should ignore case (be case-insensitive)._  
_NOTE: The `-n` flag specifies the search result should also return the line number(s) of the match(es)._  
_NOTE: The `-l` flag specifies the search result should show the file path--not the match result line itself._

## Find File - By Name

Find files in the specified path whose names match the specified glob pattern.

```shell
find <path> -name "<file_name>.*" [-type f]
```

_NOTE: The `-type` parameter defaults to `f` for file._

## Line Count

Count the number of lines in files with the specified extension.

```shell
( find . -name '*.txt' -print0 | xargs -0 cat ) | wc -l
```

## Enable Script Execution

Permit \[.sh\] file to be executed by owner.

```shell
chmod 0700 <file_path>
```

## Make Directory

Make the directory ONLY if all parent directories exist.

```shell
mkdir <directory_path>
```

## Open File Explorer

Open the system's file explorer at the specified directory.

```shell
nautilus [ssh://<username>@<ip_address>:]<directory_path>
```

_NOTE: Optionally the explorer can be made to open the directory of a remote host with the ssh prefix syntax._

## Copy File

Copy the specified file to the destination.

```shell
scp [ssh://<source_username>@<source_ip_address>:]<source_file_path> [ssh://<destination_username>@<destination_ip_address>:]<destination_file_path>
```

_NOTE: Optionally the file may be sourced from a remote host and/or sent to remote destination with the corresponding ssh prefix syntax._

## List Running Processes

List the currently running processes.

```shell
ps aux [| grep <pattern>]
```

_NOTE: Optionally list only the processes matching the specified pattern._

## End Process

Terminate the specified process.

```shell
# Graceful shutdown
slay [-<signal_name>] <process_id_or_name>
```

Alternatively,

```shell
# Terminate (abrupt shutdown)
kill [-s <signal> -p] <process_id>
```

Alternatively,

```shell
# Terminate (abrupt shutdown)
pkill [<options>] <process_pattern>
```

## Find IP Address

List network configurations. The IP addresses associated with various communications devices may be found in the response.

```shell
ifconfig
```

## Set IP Address

Set the IP address for the specified device.

```shell
ifconfig <device_name> <new_ip_address>
```

## List Binary Dependencies

List the binary dependencies for a given file.

```shell
ldd <binary_file_path>
```

## Change Password

Change the password for the current user.

```shell
passwd
```

## Check Disk Space

Show the disk space remaining.

```shell
df -ghkP
```

_NOTE: The `g` flag instructs the interpreter to display statistics in units of GB blocks. The output values for the file system statistics would be in floating point numbers as value of each unit in bytes is significantly high._  
_NOTE: For QNX, the `g` flag instructs the interpreter to display all [statvfs()](https://www.qnx.com/developers/docs/6.5.0SP1.update/com.qnx.doc.neutrino_lib_ref/s/statvfs.html) information._  
_NOTE: The `-h`/`--human-readable` flag instructs the interpreter to print the returned sizes with `K`/`M`/`G`/etc. suffixes to present the size data in a more user-friendly way._  
_NOTE: The `-k` flag instructs the interpreter to display statistics in units of 1024-byte blocks._  
_NOTE: The `-P` flag instructs the interpreter to display information on the file system in POSIX portable format (includes headings). When the -P flag is specified, the header line appears similar to:_

```shell
Filesystem 512-blocks Used Available Capacity Mounted on
```

_If the -k, -m or -g flag is specified in addition to the -P flag, the column heading 512-blocks is replaced by the respective units, depending on which of these flags is used with the -P flag.  
File system statistics are displayed on one line in the following order:_

```shell
FileSystem, TotalSpace, UsedSpace, FreeSpace, UsedPercentage, MountPoint
```

# QNX Only

The commands detailed below apply specifically to QNX-based terminals.

## List Running Processes

List the currently running processes.

```shell
pidin [| grep <pattern>]
```

_NOTE: Optionally list only the processes matching the specified pattern._

## Process Memory Usage

Print the memory currently used by the specified process.

```shell
pidin pmem | grep <process_name>
```
