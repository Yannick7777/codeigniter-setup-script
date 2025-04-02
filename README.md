## Idea
This Project aims to simplify setting up a laravel project in a local development environment for new and experienced developers.

It stores all data (excluding the built docker image) in a single directory to make it easy for a developer to remove existing projects again and keep their system clutter-free.

The only **dependencies** for this project are **git** and **docker(-compose)**.

Tested shells are: `bash`, `zsh`

## Content
This project ships with a custom docker container based on **php:8.2-apache** with the php extensions opcache, pdo_mysql, intl, and zip.

It also includes **mysql:8** and **phpmyadmin:latest**.

## Other useful info
- To reset the Database, stop the Docker containers, go to the project root and execute `rm -rf dbdata`. Then execute `./setup`.
- The apps and PMAs port can be changed by editing the `SETUP_APP_PORT` and `SETUP_PMA_PORT` variables in `.env`. This resets after running `./setup`.

## Setup
### Windows with VSCode
- If WSL isn't installed yet, install it by executing `wsl --install` in your preferred shell.
- Open WSL from startmenu or your preferred shell by executing `wsl`.
- Open VSCode by executing `code`.
- Wait until the VSCode server is installed.
- VSCode should open up. Press F1 and use `WSL: Connect to WSL` command.
- Press F1 and use `Git: Clone` to clone this repo.
- `cd` into this repo (the laravel-setup-script directory).
- Press F1 and use `Git: Clone` again. Make sure to clone it into this repo's folder and to NOT open the cloned repository and instead click `cancel`.
- Rename your project to `laravel` by either using the `mv` command in the VSCode terminal or by right-clicking on the directory in VSCode and clicking `rename`.
- Start Docker Desktop on Windows.
- Type `./setup` into the VSCode terminal.
- Type `./start` into the VSCode terminal.
- Done!
#### Tips & Tricks
- If you encounter any Docker-related issues, it might help to close Docker Engine and stop WSL by executing `wsl -t ubuntu` in your preferred shell. After that, start both again.
- If you want to commit to your laravel repo with the VSCode F1 commands, make sure to switch to the folder your repo is in first. This can be done via `File` => `Open Folder...`

### Linux
- If you're a (sigma) Linux user, follow the Windows instructions starting from when the repo should be cloned.
- Make sure you have access to the `docker` and `docker compose` commands.
- Make sure you started the Docker Daemon; that's `rc-service docker start` for Open-RC based distros and `systemctl start docker` for Systemd based distros. If you're not sure what type of distro you're running, you probably run a Systemd based one.
