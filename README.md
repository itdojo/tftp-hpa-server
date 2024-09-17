# A simple, containerized, tftp-server

For those rare occasions you need a TFTP server.

## Usage

1.  Place files you wish to be accessible via tftp in `./files` folder.
2.  Run a tftp daemon container.

```shell
docker compose up -d
```

3. Upload/Download files as desired to/from client.  See [**Client Usage**](#client-syntax).
4.  Stop and remove the container when done.

```shell
docker compose down
```

***

## Setting TFTP Variables

* You can modify TFTP variables by editing `config/tftp-hpa.conf`.  
> For general usage, you should not need to modify any settings.  Refer to the tftp-hpa manpage for variable options.

***

## Client Syntax

For MacOS and Debian/Ubuntu

- [ ] Install tftp-hpa on client.

```shell
sudo apt update && sudo apt install -y tftp-hpa
```

***

### Downloading

Syntax:

```shell
tftp <server-ip>

# Get single file
get <filename>

# Get <remotefile> file, rename to <localfile>
get <remotefile> <localfile>

# Get multiple files
get file1 file2 file3...

# Exit
quit
```

Or, all on one line:

```shell
tftp -v <server-ip> -c get <filename>
```

***

### Uploading

Syntax:

```shell
tftp <server-ip>

# Upload a single file
put <filename>

# Upload <localfile>, rename to <remotefile>
put <localfile> <remotefile>

# Upload multiple files
put file1 file2 file3...

# Exit
quit
```

Or, all on one line:

```shell
tftp -v <server-ip> -c put <filename>
```

***

## TFTP Mode

If you are using Windows you might need to specify the mode (`-m mode`) in order to preserve carriage returns, etc. for text files.  You will know this if your uploaded/downloaded file are corrupted or lose their basic formatting.  If that happens, visit https://manpages.debian.org/bookworm/tftp-hpa/tftp.1.en.html for additional info.

