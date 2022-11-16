# qmk_custom
My qmk bindings for my Keychron Q1.

It's based on [VIAL](https://get.vial.today/).

This is a WIP and to help me know where I am at in my customization.

## Info

I don't want to remap layers on via, so I made all changes to the source code. That way, if I get an other QMK keyboard, it's going to be easy to use those configurations. For it to work, **layer 0 must not be changed from default US layout**.

Maximum number of layers is 16, so I will set it up that way.

For easy reminder, you can press XXXX to launch image viewer of layer image. For it to work, put the images in ~/.qmk/layerimages/keychron-q1_0-15.png

### Keyboard layout information : 

My keyboard image here.

#### Minimal configuration :
On the left of the space bar, the following keys are there : KC_LCTL, KC_LGUI, KC_LALT 

On the right of the space bar, the following keys are there : KC_RALT, KC_APP, KC_RIGHT_CTRL

Unused modifier : KC_RIGHT_GUI 

On Keychron Q1 : Inverted L keys on top right starting from left then going down : KC_DOWN KC_INSERT KC_PRIOR KC_PAGE_DOWN KC_HOME

Keys are have the following keycaps :  PRINTSC MENU INSERT PAGEUP PAGEDOWN

## TODO
1. Get navigation keys working
2. 

Key remapping using [overrides](https://docs.qmk.fm/#/feature_key_overrides) and not using layers

  - Util
  ```
  KC_LEFT_SHIFT KC_CAPS_LOCK = [Caps Word](https://docs.qmk.fm/#/feature_caps_word)
  ACTION_TAP_DANCE_DOUBLE(KC_CAPS_LOCKS, KC_HYPER) # Tap 1 and hold 2 time to use KC_HYPER 
  ```

  - Navigation
  ```
        KC_APP KC_UP   : KC_PAGE_UP
        KC_APP KC_DOWN : KC_PAGE_DOWN
        KC_APP KC_LEFT : KC_HOME
        KC_APP KC_LEFT : KC_END
        
      
        
        # OVERWRITE KEYS IF Q1 is defined with following keycaps PRINTSC MENU INSERT PAGEUP PAGEDOWN
        KC_DEL                          : KC_PRINT_SCREEN
        MOD_MASK_SHIFT KC_DEL : KC_PAUSE
        KC_INSERT                       : KC_MENU
        KC_PRIOR                        : KC_INSERT
        KC_RIGHT_SHIFT KC_PAGE_DOWN     : KC_HOME
        KC_RIGHT_SHIFT KC_HOME          : KC_END
          
        ACTION_TAP_DANCE_DOUBLE(KC_DEL, KC_SCROOL_LOCK)
  ```

MOD-TAP :

CAPLOCK HOLD = toogle caplock layer
BACKSPACE =   



TAP-DANCE :
CAPLOCKS = 2 tap to toggle cap lock
KC_LEFT_GUI = 1 tap and hold for KC_LEFT_GUI 


Keyhold :
FXX = FXX + 12


del = SHIFT + BACKSPACE
end =


## Keyboard layout

### 0_base_us_ansi : qwerty

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


### _keypad : keypad mode 
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
        KC_APP KC_SLASH : KC_KC_CALCULATOR
        
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
