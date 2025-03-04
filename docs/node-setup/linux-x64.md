# Setting up Ubuntu (x64) Node Environment

## XRDP

### Installation

On the remote machine, execute:
```bash
sudo apt install xrdp
```

### Environment Variables

Modify either `~/.xsessionrc` or `/etc/xrdp/startwm.sh` (recommended) and add the following lines at the very top:
```bash
export GNOME_SHELL_SESSION_MODE=ubuntu
export XDG_CURRENT_DESKTOP=ubuntu:GNOME
```

These commands assume Ubuntu with GNOME Desktop.

Reboot the remote machine to apply changes.

### Permissions

XRDP may require additional user permissions. Lack of access may lead to a blank screen. To fix this, run:
```bash
sudo adduser xrdp ssl-cert
```

This adds the `xrdp` user to the `ssl-cert` group for SSL certificate permissions.

Reboot the remote machine to apply changes.

### Enable D-Bus

D-Bus is essential for applications communication. To avoid issues, run:
```bash
sudo apt install dbus-x11
dbus-launch
```

These commands install `dbus-x11` for XRDP and launch a new D-Bus session.

## Launching an XRDP Session

For Windows users, use Remote Desktop Connection. Click 'Show Options' and enter the IP address and user name. Click 'Connect'.

Enter the user's password and click 'Allow me to save credentials' if desired. Leave the 'Session' field unchanged.

Click OK to connect. If issues arise, review the steps above.

## Playwright

Now connected via XRDP, you can install Playwright. Use SSH instead of XRDP for installation. Connect via `ssh <username>@<IP-address>`.

Follow standard Playwright installation instructions [here](../getting-started/web-testing/playwright-linux.md).

## Jenkins

### Create New Device

Create a new device on Jenkins. To make the agent script work, add `dsstbautomate 10.34.16.11` to `/etc/hosts`. This ensures Linux recognizes 'dsstbautomate' as the Jenkins site alias.

### Agent

<!-- Agent setup instructions -->

## References

1. https://devicetests.com/fix-xrdp-login-blank-screen-issues
