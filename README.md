<h1 align="center">File Browser Packaging for Linux</h1>

<p align="center">
  <!-- License -->
  <img src="https://img.shields.io/github/license/To-The-Universe/filebrowser-packaging-for-linux">
  <!-- Latest Release -->
  <img src="https://img.shields.io/github/v/release/To-The-Universe/filebrowser-packaging-for-linux">
  <!-- Total Downloads -->
  <img src="https://img.shields.io/github/downloads/To-The-Universe/filebrowser-packaging-for-linux/total">
  <!-- DEB / RPM Packaging -->
  <img src="https://img.shields.io/badge/package-DEB%20%7C%20RPM-green">
  <!-- Platform Support -->
  <img src="https://img.shields.io/badge/platform-AArch64%20%7C%20RISC--V64%20%7C%20AMD64-blue">
</p>

This project is a fork of the [filebrowser/filebrowser](https://github.com/filebrowser/filebrowser) project.

It provides installation packages for Debian (.deb) and Fedora (.rpm) Linux systems on AArch64, RISC-V64, and AMD64 architectures.

:warning: **Only tested on Debian 13 (AArch64)** :warning:

---

## Usage

1. Start the service:
    ```bash
    sudo systemctl start filebrowser.service
    ```

2. **Note:** Retrieve the randomly generated administrator password created during the first service startup:
    ```bash
    journalctl -u filebrowser.service -b --no-pager -o cat --grep="initialized with randomly generated password" | tail -n1 | awk -F'password: ' '{print "initializ password:" $2}'
    ```

3. Access the Web interface:
    * Default address: `http://YOUR_SERVER_IP:59230`
    * Log in using the `admin` username and the password shown in the logs.

---

## Uninstallation

### Standard Uninstall
> Removes the application binary.

Debian:
```bash
sudo apt remove filebrowser
```

### Full Uninstall
> Removes the application binary, `/etc/filebrowser.db`, `/etc/filebrowser.json`, `/etc/filebrowser/` (if empty), and the `filebrowser` system user and group.

Debian:
```bash
sudo apt purge filebrowser
```

---

## Other Default Attributes

| Attribute        | Description                          |
|------------------|--------------------------------------|
| User & Group     | `filebrowser:filebrowser`            |
| Root Directory   | `/mnt/filebrowser/` (775)            |
| Configuration    | `/etc/filebrowser/filebrowser.json`  |
| Database File    | `/etc/filebrowser/filebrowser.db`    |
