# Munbyn ITPP130B Linux CUPS Driver (PPD)

This repo contains a working CUPS PPD driver for the Munbyn ITPP130B thermal label printer for Linux systems.

## The Problem
Munbyn officially provides a Linux driver (PPD) for their ITPP129B model, but if you plug in the newer ITPP130B, Linux dosent always recognize it properly out of the box. You usually end up with an "Unknown Device" or generic text printer setup that ruins the label formatting.

## The Solution
Both the 129B and the 130B use the exact same 203 DPI thermal print head and underlying rasterizer (`rastertolabeltspl`). 

I took the official 129B PPD file and modified the OS-level metadata headers. This forces Linux and the CUPS print spooler to officially recognize the ITPP130B by its actual model name and apply the correct page sizes and thermal settings without breaking the print formatting.

## Installation Instructions

You can install this through your standard Linux settings or via the CUPS Web Interface.

### Method 1: Standard Linux Settings (Ubuntu, Mint, etc.)
1. Download the `Munbyn-ITPP130B.ppd` file from this repo.
2. Plug in your printer via USB and turn it on.
3. Open your system's **Printers** settings.
4. Click **Add Printer**.
5. Select the Munbyn printer from the list of local USB devices.
6. When asked for a driver, choose **Provide PPD file** (or similar option depending on your distro).
7. Select the downloaded `Munbyn-ITPP130B.ppd` file.
8. Apply and print a test page!

### Method 2: CUPS Web Interface
1. Download the `Munbyn-ITPP130B.ppd` file.
2. Open your web browser and go to `http://localhost:631`
3. Go to the **Administration** tab and click **Add Printer**.
4. Select your Munbyn USB printer from the "Local Printers" list.
5. Click Continue until you reach the "Provide a PPD File" section.
6. Upload the `Munbyn-ITPP130B.ppd` file and click **Add Printer**.
7. Set your default paper size (e.g., 4x6 or 57x40mm) in the default options.

## Disclaimer
This is an unofficial community fix. I don't work for Munbyn, so use this at your own risk. Im just a developer who needed this printer to work properly on a Linux point-of-sale system and figured someone else might need the fix too.
