
# Programming and setup for your MechKeys AVR-based board

Every MechKeys.ca board ships pre-programmed and ready to use.

To enhance the original layout on the board, download the pre-programmed layout from the board, modify it in the Boot Mapper Client, and upload it to the board.

In most cases, you will not need to upload new firmware to the board.

## tl;dr
* Get the bootmapper client, firmware, and extract both
* Plug your board in
* Run the bootmapper client
* Transfer the current layout from the board to the bootmapper client
* Pick the action you want in the "spreadsheet" list of available key actions
* Click the key on the keyboard rendering at the bottom to map the action to the key
* Rinse and repeat
* Enable the "reboot after uploading" checkbox
* Click upload


## Downloads
Download both the client and the firmware.

### BootMapper Client
* Windows BootMapper Client: https://www.dropbox.com/s/3bn9flirkb49ahz/BootMapperClient.zip?dl=0
* Mac OSX BootMapper Client: https://www.dropbox.com/s/wselndg19ofby85/BootMapperClient.mac.zip?dl=0

### Firmware
PS2avrGB: https://github.com/showjean/ps2avrU/releases

Select the file named "ps2avrGB_firmware_Vx.x.x_YYMMDD.zip"

Do NOT select the file "ps2avrGB4U_firmware_Vx.x.x_YYMMDD.zip"

### Extract the files

Extract the BootMapper Client zip file.
Extract the ps2avrGB_firmware zip file.

#### Firmware files
| File                    | Purpose                    |
|-------------------------|----------------------------|
| ps2avrGB_NKRO.hex       | MechKeys keyboard firmware |
| ps2avrGB_split_NKRO.hex | Unused                     |
| keymap/                 | Directory of keymaps       |
| keymap_gb_B8000.hex     | Unused                     |
| keymap_gb_EN_B87(EX)_mini(EX).hex | Base keymap for TKL, ALU84 |
| keymap_gb_EN_face_thumb(R)(X2).hex | Base keymap for 60% |
| keymap_gb_pad.hex        | Base keymap for MechPad | 
| dualaction/              | Unused |


## Mapping Keys
1. Start the BootMapper Client
1. Connect the board
1. Click the “Key Mapper” tab
1. Click "Download", which will copy the existing keymap from the board to the Boot Mapper Client
1. For each key that you wish to change:
  2. Click "Toggle Bootmapper"
  1. On the keyboard diagram at the bottom of the Boot Mapper Client, click the key to change
  2. Click the key that has the action you wish the first key to have
  3. Click "Toggle Bootmapper"
1. Repeat for all keys and all layers
2. Click "Save keymap_part.hex" to save your keymap file to disk
3. Click Upload to transfer the new keymap to your keyboard


## Setting RGB LEDs
1. Start the BootMapper Client
1. Connect the board
2. Click the "Options" tab
1. Click "Connect"
  1. Note: the LEDs will not turn on until after you click "Disconnect"
1. Modify LED settings

| Setting | Effect |
|---------|--------|
| Num of RGB LEDs | The number of RGB LEDs on the PCB |
| RGB LED mode selection and color setting | Choose between "off", "Rainbow", or a solid color. | 
|                                          | Explicit Rainbow colors may be defined using hexadecimal codes |
| RGB LED Brightness | Controls RGB LED. Note that the brighter the RGB LED, the dimmer the switch LEDs will be |
| RGB LED key event selection and color setting | |
| Full LED Mode | |
| Lock LED Settings | Specify lighting for "Num Lock", "Caps Lock", and "Scroll Lock" |


## Custom Macros 
You can define a maximum of 12 Custom Macros.
A macro can have up to 42 characters.

### Macro overview
1. Start the BootMapper Client
1. Connect the board
2. Click the "Custom Macro" tab
3. Select the desired Custom Macro button
  1. E.g "CstMac1"  
4. Enter the characters you want for your macro
5. Click "Save macro.hex"
6. Click Upload

### Combined Keys
Example: Creating a macro for "ctrl+c"

1. Click "LCtrl" on the keyboard diagram to add it to the Macro Builder section in the middle of the Custom Macros screen.
2. Select the "LCtrl" in the Macro Builder section
3. Click the "Split" button 
4. This "splits" the macro into "LCtrl [down]" and "LCtrl [up]"
5. "Down" means "when the key is pressed down", and "up" means "when the key is released"
6. Select "LCtrl [down]"
7. Click the "C" button on the keyboard diagram
8. Save and upload

### Macro delays
1. Click the desired key
2. Enter the duration (min: 0.1s; max 5s) 
3. Click “Apply delay”

### Text To Macro
1. Enter the text to be used as a macro in the "String Parsing" text box 
2. Click “Parse string >>” to automatically split the text and place it in the Macro Builder 

#### Available texts 
```
Normal Texts : `1234567890-=qwertyuiop[]\asdfghjkl;'zxcvbnm,./
Shift+Texts : ~!@#$%^&*()_+QWERTYUIOP{}|ASDFGHJKL:"ZXCVBNM<>?
```


## Uploading Firmware

NOTE: This is not required for the normal operation of a MechKeys keyboard. 

1. Start the BootMapper Client
1. Connect the board
1. Click the “Options" tab
2. Click "Firm Up(select hex file)”
3. Select firmware file.
4. The keyboard will restart

### Firmware failure
If the bootloader fails to start

1. Press and hold the "Left CTRL" key (for the MechPad, press and hold the “0” key)
2. Connect USB cable 
3. Release the "Left CTRL" key
4. The bootloader will start
