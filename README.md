<div align="center">
  <h1><b>
   Systemctl Timers For Pihole Updates
  </b></h1>
</div>

## Overview

This README provides instructions for installing and using the pihole-updatePihole and pihole-updateGravity systemctl timer services for Pi-hole. These services automate the process of updating Pi-hole and updating the gravity list on a regular basis, using Pi-hole's built-in commands.

## Prerequisites
Before proceeding with the installation, make sure you have the following:

- A Linux-based system (such as Raspberry Pi) running Pi-hole.
- Basic knowledge of the Linux command line.
- Administrative access to the system.

## Installation

### Step 1: Accessing the Command Line

Ensure that you have access to the command line interface of your Pi-hole system. This can be done by either physically connecting a keyboard and monitor to the system or by accessing it remotely via SSH.

### Step 2: Setting Up Systemctl Timer Services

Open a terminal or SSH session and move the required files to the `/usr/lib/systemd/system/` directory.

```console
sudo mv -vf pihole-* /usr/lib/systemd/system/
```

### Step 3: Enabling and Starting the Timer Services

Using for following command to enable the timer services.

```console
sudo systemctl enable --now pihole-updateGravity.timer pihole-updatePihole.timer
```

## Customization

To customize the update frequency or make other changes to the systemctl timer services, you can use the `systemctl edit` command. This allows you to modify the service configuration without directly editing the original files.

### Step 1: Open the Service Configuration

To edit the `pihole-updatePihole` or `pihole-updateGravity` service/timer configuration, run the following command by opening a terminal or SSH session.

I.E. to edit the `pihole-updatePihole.timer`

```bash
sudo systemctl edit pihole-updatePihole.timer
```

### Step 2: Make the Desired Changes

The systemctl edit command opens the configuration file in your default text editor.

Modify the content of the file as needed following the instructions displayed. For example, to change the update frequency, you can modify the `OnCalendar` line.

Save and close the file. The modified configuration will be stored in a separate override file.

### Step 3: Apply the Changes

To apply the changes and make them effective, reload the systemctl daemon:

```bash
sudo systemctl daemon-reload
```
To apply the changes and make them effective, reload the systemctl daemon:

Copy code
sudo systemctl daemon-reload
Restart the timer service to apply the modified configuration:

Copy code
sudo systemctl restart pihole-updatePihole.timer
sudo systemctl restart pihole-updateGravity.timer
The services will now use the updated configuration.

Note: Using systemctl edit creates an override file that takes precedence over the original service configuration. If you need to revert the changes, you can simply delete the override file using the `systemctl revert` command followed by the service name.

## Conclusion

By following the steps outlined in this README, you have successfully installed and configured the pihole-updatePihole and pihole-updateGravity systemctl timer services for automating Pi-hole updates. These services will ensure that your Pi-hole installation remains up to date with the latest versions and gravity lists, providing a more secure and efficient ad-blocking experience.