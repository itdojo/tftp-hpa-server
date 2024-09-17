# A simple, containerized, tftp-server

For those rare occassions you need a TFPT server.

## Running the container

1.  Place files you wish to be accessible via tftp in `./files` folder.
2.  Start the container.

```shell
docker compose up -d
```

3. Upload/Download files as desired.  See [**Client Usage**](#client-usage) for client syntax.

***

## Stop and remove the container

```shell
docker compose down
```

***

## Setting TFTP Variables

* You can modify TFTP variables by editing `config/tftp-hpa.conf`.  
> For general usage, you should not need to modify any settings.  Refer to the tftp-hpa manpage for variable options.

***

## Client Usage

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

get <filename>
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

put <filename>
```

Or, all on one line:

```shell
tftp -v <server-ip> -c put <filename>
```

***
