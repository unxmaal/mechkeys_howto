
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
Windows BootMapper Client: https://www.dropbox.com/s/3bn9flirkb49ahz/BootMapperClient.zip?dl=0
Mac OSX BootMapper Client: https://www.dropbox.com/s/wselndg19ofby85/BootMapperClient.mac.zip?dl=0

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





6. Custom Macro 
You can define maximum 12 Custom Macros.
A macro can have up to 42 characters.

1) Start bootMapper Client progrma

2) Select “Custom Macro” tab.





3) You can see the display below
Select CstMacX tab(CstMac stands for “Custom Macro”.) and enter Characters you want. 
You can delete a selected character by pressing “remove” button.
You can change order by dragging a character.




4) Select “save macro.hex” to save Macro setting.
When you upload this file to keyboard using bootloader.

5) If you want to combine modifier keys as a macro, follow the instructions.(Example shows how to set “Ctrl+c” macro.)
Add all the keys you want to use as a macro.





- While LCtrl selected, press the “split” button.(or shift + mouse click)






- You will see the splited LCtrl into down and up. 





- Just drag anything to place “C” is in the middle between LCtrl(down) and LCtrl(up).









6) You can set the delay for a macro.
- Selecte the key you want.
- Enter time(min 0.1 sec, max 5 secs) 
- Press “apply delay” button









7) Text To Macro
The text entered can be translated into a macro

- Enter the text you want to us as a macro in the text box "String Parsing" 



press “parse string >>” button, and then you can see all the keys splited.




- Available texts 
Normal Texts : `1234567890-=qwertyuiop[]\asdfghjkl;'zxcvbnm,./
Shift+Texts : ~!@#$%^&*()_+QWERTYUIOP{}|ASDFGHJKL:"ZXCVBNM<>?


3. How to upload firmware

Supporting both for Window and Mac OS
Available only while connected by USB
First of all you must upload firmware to enable all the functions properly.(When MCU was attached to the PCB by soldering, bootloader was automatically installed.)

Start bootMapperClient.exe

2) Select “Options > firm up(select hex file)” and select firmware file.











- After automatically starting bootloader, keyboard works again. 
- If bootloader doesn’t start again, you have to start in manually. While pressing the key “Left ctlr”(in case of B.pad the key “0”), connect USB cable. Then bootloader will start again.
