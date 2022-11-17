# qmk_custom
My qmk bindings for my Keychron Q1.

It's based on [VIAL](https://get.vial.today/).

This is a WIP and to help me know where I am at in my customization.

## Info

The MCU in Q1V1 is small awith limited MCU flash. So only the 4 first layers can be dynamic and 4 more programmed in code. My system is Linux, so no Mac/Win things.

TODO: For easy reminder, you can press XXXX to launch image viewer of layer image. For it to work, put the images in ~/.qmk/layerimages/keychron-q1_0-15.png

### Keyboard layout information : 

My keyboard image here.

#### Minimal configuration :
On the left of the space bar, the following keys are there : KC_LCTL, KC_LGUI, KC_LALT 

On the right of the space bar, the following keys are there : KC_RALT, KC_APP, KC_RIGHT_CTRL

Unused modifier : KC_RIGHT_GUI 

On Keychron Q1 : Inverted L keys on top right starting from left then going down : KC_DEL KC_INSERT KC_PRIOR KC_PAGE_DOWN KC_HOME

Keys are have the following remap and keycaps :  KC_PRINT_SCREEN KC_MENU KC_INSERT KC_PAGE_UP KC_PAGE_DOWN [DONE]

## Build env
I had trouble to setup on Fedora 36 so here is how I did it.

`sudo dnf install git python3-pip`
`python3 -m pip install --user qmk`
`echo 'PATH="$HOME/.local/bin:$PATH"' >> $HOME/.bashrc && source $HOME/.bashrc`

## Build Q1 with vial support
`make keychron/q1/rev_0100:vial`
`make keychron/q1/rev_0100:vial:flash`

### For vial-gui
pip install setuptools=57.5.0
sudo dnf install libusb-devel systemd-devel






## Keyboard layout

### 0 L_BASE : qwerty
Normal layer in US

### 1 D1_FN : Dynamic layer #1 for vial
### 2 D2_FN : Dynamic layer #2 for vial
### 3 D3_FN : Dynamic layer #3 for vial


### 4 N_FN : Navigation and numpad layer
Pressing KC_APP | KC_SLASH toogle a numpad over the letters. 

Holding KC_CAPS momentarely enables navigation layer

Status : WORK

TODO: RGB
TODO : disable all other incompatible layers



### 3_M_FN : Multimedia layer 
Pressing KC_TAB FIXME

### 4_NAV_FN : Navigation layer
Pressing KC_APP | KC_ENTER toogle navigation layer



- FXX row get +12
- Arrows are changed

### 5_DMAC_FN : Dynamic macro record and play
Pressing KC_APP | KC_MENU toogle macro layer

- KC_PRINT_SCREEN : paste macro 1
- KC_INSERT : record macro 1
- KC_PGUP : record macro 2
- KC_PGDN : paste macro 2
- KC_MENU : finish recording macro

### 8 S_FN : System layer
Pressing KC_APP | KC_RIGHT_CTRL wil momentarely enable system layer

- KC_ESC : power off
- KC_PGUP : wake
- KC_PGDN : sleep
- KC_PRINT_SCREEN : KC_SYRQ 


## Special keys and combinations

### Copy Cut Paste
Just hold KC_C KC_X KC_V and it will add the KC_RIGHT_CTRL automaticaly.

### CAP WORD
KC_LEFT_SHIFT KC_RIGHT_SHIFT OR double tap KC_SHIFT = [Caps Word](https://docs.qmk.fm/#/feature_caps_word)



## OLD

### 3_caplock

 <details>
  <summary>### _mouse</summary>
### _mouse
Not a priority, in backlog.

Set backlight to red for virtual mouse while the layer is activated.

Use **q-w-e-a-d-z-x-c** for mouvement, **s** or **1** for left click, **2** for middle click, **3** for right click and **KC_GRV** **`** to exit mouse mode.

(smooth arrow)[https://www.reddit.com/r/olkb/comments/72u8ou/qmk_mouse_keys_rock/]
</details>

### _left_arrows : wasd as arrows


### _keypad : keypad mode [TO TEST]
        Set backlight to blue for virtual keypad while the layer is activated. 
        u=6 i=5 o=5 j=3 k=2 l=1 ,=0 ==+ 
        
### _media : multimedia macro
  - Multimedia
  ```
  KC_KB
  ```
### _fxx : Function row macro
  Hold KC_APP KC_RIGHT_CTRL
  ```
  KC_APP KC_RIGHT_CTRL KC_F1 : KC_F13
  ...
  KC_APP KC_RIGHT_CTRL KC_0 : 
  KC_APP KC_LS
  
  ```


### _term : terminal macro
### _wm : window manager macro 
### _vi : vi mode style macro

### _fn : Function row macro
  Hold KC_APP KC_RIGHT_CTRL
  ```
  MT(, KC_F1) : KC_F13
  ...
  ```

### 14_fn
Hold **KC_APP** while pressing a key 

 - Toogle
  ```
        KC_APP KC_TAB : toogle rgb on/off
        KC_APP KC_KACKSLASH : KC_NUM_LOCK
  ```
  
  - Application
  ```
        KC_APP KC_SLASH : KC_CALCULATOR
        
  ```

  
 
  
  - QMK backlight
  ```
  
  ```
  

### 15_super_fn : function layer for keyboard management
To toogle layer hold **KC_RIGHT_GUI KC_APP KC_RIGHT_CTRL**

  - SAFE
  ```
  KC_APP KC_ : layer_clear() # Clears all layers (turns them all off).
  ```
 
  
  - [QMK](https://docs.qmk.fm/#/quantum_keycodes/)
  
  ```
  : QK_REBOOT # Resets the keyboard. Does not load the bootloader
  : QK_BOOTLOADER # Put the keyboard into bootloader mode for flashing
  : QK_CLEAR_EEPROM # Reinitializes the keyboard’s EEPROM (persistent memory)
  : QK_DEBUG_TOOGLE # Toggle debug mode
  ```
  
  - Commands system
  ```
        KC_APP KC_ESC : KC_SYSTEM_SLEEP
        KC_APP KC_LEFT_SHIFT KC_ESC : KC_SYSTEM_POWER
        KC_APP KC_LEFT_CRTL KC_ESC : KC_SYSTEM_WAKE
        : KC_SYSTEM_REQUEST
        : 
  ```
  (KC_SYSTEM_REQUEST)[https://www.thegeekstuff.com/2008/12/safe-reboot-of-linux-using-magic-sysrq-key/] 
  
  CUSTOM KEYCODES
  5x KC_LEFT_CTRL KC_LEFT_ALT KC_DELETE: 
  <details>
  <summary>Safe reboot by sending multiple keys</summary>
  
  ```
  KC_LEFT_ALT KC_SYSTEM_REQUEST KC_LEFT_SHIFT KC_R
  KC_LEFT_ALT KC_SYSTEM_REQUEST KC_LEFT_SHIFT KC_E
  KC_LEFT_ALT KC_SYSTEM_REQUEST KC_K 
  KC_LEFT_ALT KC_SYSTEM_REQUEST KC_LEFT_SHIFT KC_S
  KC_LEFT_ALT KC_SYSTEM_REQUEST KC_LEFT_SHIFT KC_U
  KC_LEFT_ALT KC_SYSTEM_REQUEST KC_LEFT_SHIFT KC_B
  ```
  
  </details>
  
  
  References :
  [custom shift keys](https://getreuer.info/posts/keyboards/custom-shift-keys/index.html)
  [macros](https://getreuer.info/posts/keyboards/macros/index.html)
  [layer lock](https://getreuer.info/posts/keyboards/layer-lock/index.html)
