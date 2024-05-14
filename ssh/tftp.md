# TFTP (Trivial File Transfer Protocol)

Transfer file from/to remote PC

> TFTP transfers files to and from a remote computer, typically a computer running UNIX, that is running the Trivial File Transfer Protocol (TFTP) service or daemon. TFTP is typically used by embedded devices or systems that retrieve firmware, configuration information, or a system image during the boot process from a TFTP server, says TechNet.

# Install

## Window [^1]

TFTP is disabled by default in Windows

1. Open Program install and uninstall

    * press <kbd> win </kbd> + <kbd> R </kbd> to open Run dialog

    * type "**appwiz.cpl**" and press <kbd> Enter </kbd>

2. On the left-side bar, will found the **Turn Windows features on or off**, and click it

3. Search for **TFTP client**

    * mark it for enable, if didn't enable

4. start install the TFTP client as indicate _Apply changes_, until display _Windows completed the requested changes_

5. Successfully enabled **TFTP client**

6. Testing tftp is enabled

    ```powershell
    tftp
    ```

### tftp usage:

[tftp command usage](https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/tftp)

[^1]: tftp enable on windows. Reference link: [TFTP on windows ](https://www.thewindowsclub.com/enable-tftp-windows-10#:~:text=To%20enable%20the%20TFTP%20client%20in%20Windows%2011%2F10%2C,Client.%20Check%20the%20box%20and%20click%20on%20OK.)
