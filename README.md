# Karabiner-Elements-JSON-Code
Personal key mappings for use with the Karabiner-Elements mapping software for macOS. Specifically useful for using a WindowsOS associated keyboard with macOS systems.

---------

[Karabiner Elements](https://karabiner-elements.pqrs.org) is a utility to help macOS users change keybinds. There are a few other utilities that can do this. Mainly [Automator](https://support.apple.com/guide/automator/welcome/mac) will allow you to map actions to specific key sequences. This can be done in Karabiner using [Complex Modifications](https://ke-complex-modifications.pqrs.org) or simple modifications. 

Complex modifications differ from simple modifications in a few ways. First, a complex modification is capable of mapping a sequence of keystrokes to one button whereas a simple modification is not. For example, the traditional "Print Screen" button on WindowsOS keyboards does not naturally take a screenshot of your macOS desktop. However, it's possible to map several keystrokes (shift + command + 3) to one button. [See "Print Screen Complex Modifications" from master branch]. Second, complex modifications require creating or downloading code to specifically map a sequence of keystrokes. Simple modifications do not. Lastly, it's possible to add timing for keystrokes with complex modifications. For example, it's possible to configure the previously mentioned "Print Screen" button to act as "shift + command + 4" (user defined area for screenshot on macOS) if held down for more than two seconds. 

Complex modifications are very useful and follow a simple syntax. This file aims to explore the basic syntax.

# Profiles

It's possible to create distinct profiles for working in different utilities. For example, I have a specific profile for when working in VIM or Nano. 

# Simple Modifications Instructions

https://karabiner-elements.pqrs.org/docs/manual/configuration/configure-simple-modifications/

# Pre-Built Complex Modifications

https://ke-complex-modifications.pqrs.org

# Writing You Own Code

[Complex Modification Operators](https://karabiner-elements.pqrs.org/docs/json/complex-modifications-manipulator-definition/) are the basic syntax for Karabiner Elements. Rules, examples, and simple scripts can be found in 

~~~~~~~~~~~~~~
~/library/Application Support/org.pqrs/Karabiner-Elements
~~~~~~~~~~~~~~

# Installing Complex Modifications

- [Downloading](https://karabiner-elements.pqrs.org/docs/manual/configuration/configure-complex-modifications/) from another [site](https://ke-complex-modifications.pqrs.org)
- [Database for submitting personal code](https://github.com/pqrs-org/KE-complex_modifications) offers a lot of thie same material.

I started working on this guide for this sole purpose, as it was not apparent how to install personal code. I created a .json file from [XCode](https://developer.apple.com/xcode/) (11.7). First, New Project -> macOS -> command line tool. Save to wherever, change filename to .json. Easy to edit in XCode if you have before.

Assuming you have something like:

my-bitchin-code.json

Then:
~~~~~~~~~~~~~~~
%sudo% cp filename_path/my-bitchin-code.json ~/.config/karabiner/assets/complex_modifications
~~~~~~~~~~~~~~~
Alternatively, open Karabiner, select menu item Misc, bottom right select "Open config folder ...", copy and paste my-bitchin-code.json into folder "complex-modifications". Don't forget to restart Karabiner-Elements after you copy in your code. This is a good place to store development code. However, to properly instasll the code it must be put into the "karabiner.json" file found in the above extension. Here is a quick before and after for where you would import a complex modification into the karabiner.json document.

BEFORE:
~~~~~~~~~~~~~~~~~~
{
    "global": {
        "check_for_updates_on_startup": true,
        "show_in_menu_bar": true,
        "show_profile_name_in_menu_bar": true
    },
    "profiles": [
        {
            "complex_modifications": {
                "parameters": {
                    "basic.simultaneous_threshold_milliseconds": 50,
                    "basic.to_delayed_action_delay_milliseconds": 500,
                    "basic.to_if_alone_timeout_milliseconds": 1000,
                    "basic.to_if_held_down_threshold_milliseconds": 500,
                    "mouse_motion_to_scroll.speed": 100
                },
            },
            "devices": [],
            ...
~~~~~~~~~~~~~~~~~~
AFTER: (import to line 67)
~~~~~
{
    "global": {
        "check_for_updates_on_startup": true,
        "show_in_menu_bar": true,
        "show_profile_name_in_menu_bar": true
    },
    "profiles": [
        {
            "complex_modifications": {
                "parameters": {
                    "basic.simultaneous_threshold_milliseconds": 50,
                    "basic.to_delayed_action_delay_milliseconds": 500,
                    "basic.to_if_alone_timeout_milliseconds": 1000,
                    "basic.to_if_held_down_threshold_milliseconds": 500,
                    "mouse_motion_to_scroll.speed": 100
                },
            "rules": [
                {
                    "description": "print_screen to command+shift+3",
                    "manipulators": [
                        {
                            "from": {
                                "key_code": "print_screen"
                            },
                            "to": [
                                {
                                    "key_code": "3",
                                    "modifiers": [
                                        "left_command",
                                        "left_shift"
                                    ]
                                }
                            ],
                            "type": "basic"
                        }
                    ]
                }
            ]
            },
~~~~~
You would have to do this same change for each profile in Karabiner-Elements.

Notes
- it's possible to have multiple files with different rules in each. Although, it's a lot easier to have one concise file. 
- you still have to toggle on your code options in Karabiner-Elements under menu option Complex Modifications

# Examples

PRINT SCREEN BUTTON
- In macOS the combination "shift + command + 3" will take a screen shot. Example code: [Screen Shot]( ... )
- Similarly, "shift + command + 4" will let the user define the area of a screen shot. This is mapped to the same "Print Screen" button, however, "shift + Print_Screen" will now give the user the same effect. [User Defined Screen Shot]( ... )

VIM EDITOR
- The [VIM Cheat Sheet](https://www.worldtimzone.com/res/vi.html) I use has some incredible resources. I created a custon [VIM Profile]( ... ) specifically for when I'm working in VIM. 

For example, I hate the h,j,k,l for cursor movement. This movement has been mapped to w,a,s, and d because it feels more natural, especially if you've spent anytime gaming on a PC. These are simple modifications
~
ifbgcisbce
~
ckoincowenw
