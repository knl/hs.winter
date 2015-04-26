# Mjolnir.winter

A module for moving/resizing your windows using a fluent interface (see Usage below).

The name winter is a portmanteu of **win**dow mas**ter**.

## Usage

    local winter = require "winter"
    local win = winter.new()
    

    local cmdalt  = {"cmd", "alt"}
    local scmdalt  = {"cmd", "alt", "shift"}
    local ccmdalt = {"ctrl", "cmd", "alt"}

    -- make the focused window a 200px, full-height window and put it at the left screen edge
    hotkey.bind(cmdalt, 'h', win:focused():wide(200):tallest():leftmost():place())

    -- make a full-height window and put it at the right screen edge
    hotkey.bind(cmdalt, 'j', win:focused():tallest():rightmost():place())

    -- full-height window, full-width window, and a combination
	hotkey.bind(scmdalt, '\\', win:focused():tallest():resize())
	hotkey.bind(scmdalt, '-', win:focused():widest():resize())
	hotkey.bind(scmdalt, '=', win:focused():widest():tallest():resize())

    -- push to different screen
    hotkey.bind(cmdalt, '[', win:focused():prevscreen():move())
    hotkey.bind(cmdalt, ']', win:focused():nextscreen():move())

*NOTE*: One must start with `win:focused()` or `win:window('title')`
and end with a command `move()`, `place()`, `resize()`, or `act()`
(they are all synonyms for the same action). This chain of commands
will return a function that one can easily pass to hotkey.bind.

## Todo

- [x] vcenter/hcenter (done in 8c983c59b4593259e6aa4b3c714001227f58ec8b)
- [x] improve screen handling (done in 5851cbe)
- [ ] tests
- [ ] do a proper documentation, as the one coming with mjolnir is painfull
