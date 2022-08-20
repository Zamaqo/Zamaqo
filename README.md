# Zamaqo

## Planetscale Command Reference

### Installation *(Windows)*:
> Requires scoop to be installed via powershell with the following commands:
```bash
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser # Optional: Needed to run a remote script
irm get.scoop.sh | iex
```
Install `pscale` with the following commands:
```bash
scoop bucket add pscale https://github.com/planetscale/scoop-bucket.git
scoop install pscale mysql
```
To upgrade to the latest version:
```bash
scoop update pscale
```

### **Basic usage:**
> The terminal needs to be verified with the following command:
```bash
pscale auth login
```
**Listing** possible organizations:
```bash
pscale org list
```
**Switching organizations** to access different databases:
```bash
pscale org switch <organization-name>
```
**Locally copy** a database branch *(dumping the database)*:
```bash
pscale database dump <database-name> <branch-name>
```

**Restoring** a database branch from a local copy *(restoring the dumped database)*:
> The directory flag `--dir` needs to point to the location of the local files relative to the terminal  
> an optional flag `--overwrite-tables` can be specified to wipe existing data
```bash
pscale database restore-dump <database-name> <branch-name> --dir <relative-directory>
```
