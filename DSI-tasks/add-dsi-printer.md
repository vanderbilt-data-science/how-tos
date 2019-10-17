# How to connect to the DSI network printer

This file will detail the steps for Windows and MacOSX computers to connect to the DSI networked printer.  Ensure that you're connected to a Vanderbilt wireless (or hardwired) network.

## Windows
To connect to the printer on Windows, execute the following steps:
1. Click the Windows button on the bottom, lower left hand corner of your screen.  Click the gear symbol (one above the power symbol) in the lower left hand corner of the menu that appears.  This should open up the `Windows Settings` dialog box.
2. Click `Devices` and in the Devices pane on the left, click `Printers and scanners`.
3. Click the gray `+` box next to `Add a printer or scanner`
4. Wait for Windows to find enough printers and scanners so that the blue `The printer that I want isn't listed` link appears.  Click this link.  You may have to scroll *very* far down the screen to find it.
5. In the `Add Printer` dialog that appears, click `Add a printer using a TCP/IP address or hostname`.  Click `Next`.
6. Enter/confirm the following settings:
- **Device Type**: Autodetect
- **Hostname or IP address**: 10.68.0.77
- [X] Query the printer and automatically select the driver to use
7.  Wait for the driver model to be detected.  Don't worry if this seems to take a while - be patient!
8.  Click `Next` or `OK` on any resultant steps.  Make sure to **click** the `Do not share this printer` option.
The printer is now installed!

## MacOSX
To connect to the printer on MacOSX, execute the following steps:
1. Press `Command`+`Space bar` to open Spotlight search.  Type `printer` and click `Printers & Scanners` in the search results.
2. At the bottom of the white box on the left hand side of the dialog box that appears, click the `+` button.
3. In the `Add` dialog that pops up, click `IP` at the top of the box.  Input/select the following fields:
- **Address**:10.68.0.77
- **Protocol**: Internet Printing Protocol - IPP
- **Name**: DSI-Printer-300 (or your own desired name)
- **Location**: Vanderbilt University
- **Use**: Generic PostScript Printer
4.  Click `Add`.
5.  If the option to select `Duplex Printing Unit` appears, click the box to select it.  Click `OK`.
The printer is now installed!

