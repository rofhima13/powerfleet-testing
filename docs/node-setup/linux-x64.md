# Setting up an Ubuntu (x64) Environment for Remote Access (XRDP)

Welcome! This guide explains how to set up an Ubuntu Linux machine (x64) so you can connect to its graphical desktop remotely from another computer (like Windows) using XRDP (Remote Desktop Protocol). This is particularly useful for accessing testing environments or development nodes.

## 1. Setting up XRDP (Remote Desktop Server)

XRDP allows you to use tools like Windows Remote Desktop Connection to see and interact with the Ubuntu desktop.

### Installation

* First, install the XRDP package. Open a terminal on the Ubuntu machine and run:

```bash
sudo apt update && sudo apt install xrdp -y
```

*(This updates your package list and installs `xrdp`)*

### Environment Configuration (for GNOME Desktop)

* If your Ubuntu uses the standard GNOME desktop environment, XRDP needs specific settings to display it correctly. You need to edit a startup configuration file. Editing `/etc/xrdp/startwm.sh` is recommended.
* Open the file with root privileges using a terminal editor like `nano`:

```bash
sudo nano /etc/xrdp/startwm.sh
```

* Add the following lines at the **very beginning** of the file, before any existing commands:

```bash
export GNOME_SHELL_SESSION_MODE=ubuntu
export XDG_CURRENT_DESKTOP=ubuntu:GNOME
export XDG_CONFIG_DIRS=/etc/xdg/xdg-ubuntu:/etc/xdg
```

*(These ensure XRDP starts the correct GNOME session)*

* Save the file (in `nano`: Ctrl+O, Enter) and exit (Ctrl+X).
* **Reboot the Ubuntu machine** for these changes to take effect:

```bash
sudo reboot
```

### Permissions Fix (Preventing Blank Screen)

* Sometimes, after connecting via XRDP, you might see only a blank screen. This is often due to permission issues related to SSL certificates used by XRDP.
* To fix this, add the `xrdp` user (which runs the XRDP service) to the `ssl-cert` group. In the terminal, run:

```bash
sudo adduser xrdp ssl-cert
```

* **Reboot the Ubuntu machine again** to apply the group membership change.

```bash
sudo reboot
```

### Enable D-Bus Communication

* D-Bus is a system message bus that allows applications to communicate with each other. XRDP relies on it. Ensure the necessary D-Bus components are running.
* Install the D-Bus X11 package:

```bash
sudo apt install dbus-x11 -y
```

* Ensure the D-Bus session is launched (this often happens automatically on login, but running `dbus-launch` manually in a terminal session doesn't hurt if troubleshooting):

```bash
dbus-launch
```

## 2. Connecting to the Ubuntu Machine via XRDP

Now that XRDP is configured on the Ubuntu machine, you can connect from another computer.

### From Windows

1. Open the **Remote Desktop Connection** application (search for `mstsc.exe`).
2. Click **"Show Options"**.
3. In the **"Computer"** field, enter the **IP address** of the Ubuntu machine.
4. In the **"User name"** field, enter your **Ubuntu username**.
5. Click **"Connect"**.
6. You'll likely see the XRDP login screen. Ensure the "Session" field is set to `Xorg` or `X11rdp`.
7. Enter your Ubuntu user's **password**.
8. Click **"OK"** to connect to the graphical desktop.

If you encounter connection problems or a blank screen, carefully review the XRDP setup steps (Installation, Environment, Permissions, D-Bus) and ensure all reboots were completed.

## 3. Installing Playwright

While you *can* use the graphical desktop via XRDP, it's generally better and more reliable to perform command-line installations like Playwright using **SSH (Secure Shell)**.

1. **Connect via SSH:** Open a terminal or PowerShell on your local machine and connect using:

```bash
ssh your_ubuntu_username@<IP-address_of_Ubuntu_machine>
```

(Replace placeholders with your actual username and the Ubuntu machine's IP address).
1. **Follow Playwright Linux Setup:** Once connected via SSH, follow the standard instructions for installing Playwright and its dependencies for Linux/Ubuntu, which can be found here:
    * [Getting Started with Playwright on Linux (Ubuntu)](../getting-started/web-testing/playwright-linux.md) (Ensure this link points to the correct guide).

## 4. Jenkins Agent Setup (Partial Info)

This section relates to configuring the Ubuntu machine as a Jenkins agent node.

### Create New Node in Jenkins

* You will need to configure this Ubuntu machine as a new agent node within your Jenkins interface.

### Hostname Resolution (`/etc/hosts`)

* For the Jenkins agent script or connection process to work correctly, the Ubuntu machine needs to be able to find the Jenkins master using its hostname (e.g., `dsstbautomate`). Add an entry to the Ubuntu machine's hosts file.
* Open the hosts file for editing:

```bash
sudo nano /etc/hosts
```

* Add a line mapping the Jenkins master's IP address to its hostname:

```text
10.34.16.11    dsstbautomate
```

*(Replace the IP address and hostname with the correct values for your Jenkins setup)*

* Save the file (Ctrl+O, Enter) and exit (Ctrl+X).

## References

* Troubleshooting XRDP Blank Screens: [DeviceTests.com Fix](https://devicetests.com/fix-xrdp-login-blank-screen-issues)
