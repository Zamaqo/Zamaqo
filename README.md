# Zamaqo

## Planetscale Command Reference

### Installation _(Windows)_:

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
pscale auth login # Note You will be logged into pscale CLI after having to verify a char/integer string via a web gui
```

**Listing** possible options:

> an optional `--web` flag can be added to open it in your browser

```bash
pscale org list # for organizations
pscale database list # for databases
pscale branch list <database-name> # for branches
```

**Switching organizations** to access different databases:

```bash
pscale org switch <organization-name>
```

**Locally copy** a database branch _(dumping the database)_:

> Optional `--output <directory-name>` can be specified relative to the terminal

```bash
pscale database dump <database-name> <branch-name>
```

**Restoring** a database branch from a local copy _(restoring the dumped database)_:

> The directory flag `--dir <directory-name>` needs to point to the location of the local files relative to the terminal  
> an optional flag `--overwrite-tables` can be specified to wipe existing data

```bash
pscale database restore-dump <database-name> <branch-name> --dir <relative-directory>
```

## Environment Setup _(Windows)_:

**Accept all the default options** when installing the following programs:

### Install Node:

> Required to run the development server

Download the latest version of [Node.js MSI Installer](https://nodejs.org/en/download/) and run it.

### Install Git:

> Required to clone a repository from GitHub

Download the latest version of [Git for Windows](https://git-scm.com/download/win) and run it.

### Install Visual Studio Code:

> Required to edit the code and run the development server

Download the latest version of [Visual Studio Code](https://code.visualstudio.com/download) and run it.

### Install PNPM:

> Required to install the dependencies

Open the terminal and run the following command:

```bash
corepack enable
corepack prepare pnpm@latest --activate
```

### Configure Git:

> Required to pull and push changes to the repository

Open the terminal and run the following commands:

```bash
git config --global user.name "Your Name"
git config --global user.email "Your Email"
git config --global --add safe.directory *
```

### Project Setup:

> Convention is to have your projects in a folder called `Builds` in your `Documents` folder

Open the project on GitHub and copy the link under the `Code` button. Then open the terminal and run the following commands:

```bash
cd ~/Documents/Builds
git clone <link> # eg. https://github.com/Zamaqo/alldesk.git
code <project-name> # eg. alldesk
```

## Configure the environment:

> Required to run the app locally

Open or create an `.env` file in your main directory and add all the required variables to it.

## Install the dependencies:

> Required to run the app locally

Open the VSCode terminal with **[Ctrl + \`]** and run the following command:

```bash
pnpm install
```

## Run the scripts:

Open the VSCode terminal with **[Ctrl + \`]** and run the following command:

```bash
pnpm dev # runs the development server
pnpm prisma db push # runs the database migrations
pnpm prisma studio # runs the database studio
```
