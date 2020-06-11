# Acknowledgments
Graphics used come from the Crestron application market, Slate theme - https://applicationmarket.crestron.com/slate-theme-documentation/

# Installation
First you will need to install node.js from https://nodejs.org

Then open a cmd window as admin and run the command;
    npm install -g @crestron/ch5-utilities-cli

# VS Code Extension
In VS Code, install the Crestron Components CH5 extension.
Close and reopen VS Code after this step.
I also install Live Server extension by Ritwick Dey, this allows the panel to be run in a browser, right click index.html in the folder view and use the 'Open with Live Server' option

# Setting up Chrome (excert from "Getting Started: Crestron CH5 Beta PDF)
Chrome Emulation of TSW-x60 Devices
While the CH5 emulator feature can emulate control system interactions, it cannot change
the view port size or pixel density to emulate TSW-x60 touch screen devices. However,
Chrome provides utilities to support mobile devices.

Use the web utilities and the settings provided below to emulate screen rendering on a
workstation to ensure that the project displays accurately on a TSW-x60 device.
Device Name Width Height Device Pixel Ratio Device Type
TSW-1060 1280 pixels 800 pixels 1 Mobile
TSW-760 1261 pixels 739 pixels 0.8125 Mobile
TSW-560 640 pixels 363 pixels 1.5 Mobile
TSW-560P 363 pixels 640 pixels 1.5 Mobile
For information on how to configure Chrome, refer to
https://developers.google.com/web/tools/chrome-devtools/device-mode/#custom.
NOTE: To ensure that the emulation is functioning correctly, refresh the Chrome web
browser after entering emulation mode.

# Setting up the project
Open the folder containing the project in VS Code.
Open a termial window in VS Code
If this is the first time using VS Code and if it says Windows Powershell at the top of the terminal window run the command;
 Set-ExecutionPolicy RemoteSigned

# Build project archive for loading to the touch panel
If you've built the project before you may need to delete the 'dist' directory from your folder, it wouldn't run for me if it already existed.
Comment out the emulator scripts or they will work on the touchpanel.

In the terminal run the command (instead of C:\CH5\CH5-Basic use the filepath of the folder the index.html file is in);
ch5-cli archive -p CH5-Test-Project -d C:\CH5\CH5-Basic -o dist

This will create the .ch5z file that needs to be loaded to the touchpanel

# Load project to touch panel
In the termial window run the command, replace  ip_address_of_touchpanel with the touchpanels IP address...;
 ch5-cli deploy -H ip_address_of_touchpanel -t touchscreen dist/CH5-Test-Project.ch5z
