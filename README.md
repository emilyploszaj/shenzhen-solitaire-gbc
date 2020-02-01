# Shenzhen Solitaire GBC
![The Shenzhen Solitaire GBC Main Menu|height=576px](https://i.imgur.com/aZCn37W.png)

Shenzhen Solitaire GBC is a Gameboy Color version of the solitaire game contained in the video game Shenzhen I/O by Zachtronics.

## Gameplay
Gameplay is designed to be nearly identical to the version included in Shenzhen I/O. However, due to the platform, there are notable differences:

* Cards are not moved with a mouse, rather, they are selected and picked up with a cursor controlled by the buttons on the Gameboy Color.
* Instructions are reworded to save space while conveying the same idea.

![The Shenzhen Solitaire GBC Gameplay Screen|height=576px](https://i.imgur.com/5qJLPGd.png)

Other than these caveats, Shenzhen Solitaire GBC performs similarly to the original game. Cards will move across the screen if they can be placed in slots at the top right of the screen without consequence, wins are counted, and the art is recreated to the best of the Gameboy Color's ability.

## Controls

| Control | Functions |
| --- | --- |
| D-pad | Moves the selection cursor to different stacks or to a different point in the stack. |
| A | Picks up or attempts to place a stack of cards. |
| B | Returns the held stack to where it was picked up. When held D-pad presses will be treated as used as many times as possible. |
| Start | Moves to the dashboard buttons to either select a new game, read the instructions with A, or return to the board with B or Start. |
| Select | Switches the cursor from the main board stacks up to the free slots and numbered card slots or vise versa |

## Restrictions
Due to the nature of the system, there are some notable restrictions to what is possible in the game.

* Since a 32 bit number is used as a seed for the random generator, only 4294967296 different deck configurations are initially possible, assuming no duplicates. This is in comparison to the 59021649540501861570139704108515328000000000 real possibilities (this means only about 0.000000000000000000000000000000000072769353778% of possible deck configurations are possible from game start). However, if multiple games are played consecutively, the number of posible games increases, as the deck is never unshuffled.
* The win counter for the game has a max value of 99999999 so if you happen to beat the game one hundred million times, your wins from that point onward will not be counted. It is important to note that assuming you lose no games and that your average game is 90 seconds long, it would take you over 285 years to reach this point, much more if you chose to do anything else for those 285 years like eating or sleeping.

## Compiling
Shenzhen Solitaire GBC uses GBDK to compile C code to Gameboy ASM. If GBDK is installed in your ``C:`` root, you can run ``build.bat`` to generate ``shenzhen-solitaire.gbc``. Otherwise, you can take the contents of the file and simply change the path of lcc. In order to use this file you will need a way to run Gameboy Color roms, this can be in the form of an emulator or a flash cart.

## Code Conventions
There are some conventions used to write this software that you should be aware of if trying to understand it.

* All variables and methods are written in ``snake_case``.
* All arrays are 1-dimensional (this is due to a bug in the lcc compiler shipped with GBDK).
* Shifts are prefered to multiplication and division operators (though, sometimes they are used when they don't need to in order to combat issues with the compiler).
* A lot of weird coding choices are probably done to prevent compiler issues.
* GBDK types are used instead of C types, for example: ``UINT8`` is used instead of ``unsigned char`` and ``INT16`` is used instead of ``short``.
* The four common data postfixes ``tiles``, ``map``, ``palettes``, and ``att`` represent tile data, indices of the tile data, tile palettes, and indices of tile data respectively.
* There no formal text tilesets, text is always displayed from a static use-specific tileset, this means text does not obey the 8x8 tile rule for individual characters.

## Credits

* Emily - All of the code in the project, most of the art, and most anything else.
* Ted Wollman - The art occupying the top half of the main menu screen.
* Zachtronics - The game Shenzhen I/O and its solitaire game which this game is attempting to immitate.
* GBDK - The library that was used to write this Gameboy Color game in C as opposed to using Gameboy ASM.