# Doom Grub Theme
A Grub2 theme in the style of Doom!

## Installation
- `cd /boot/grub2/themes/` and do `git clone https://github.com/Lxtharia/doomgrub-theme.git`
- change/add this line in your /etc/default/grub:

```GRUB_THEME=/boot/grub2/themes/doomgrub-theme/theme.txt```
- `grub2` might be called `grub`, but there should be no difference 
- update your live grub config by running `sudo grub-mkconfig -o /boot/grub2/grub.cfg`
- your good to go

## Cool
- You probably didn't think "Wait, but how is this possible", probably because you never made a grub theme with a custom font
- The thing is:
- Grub can only use **bitmap fonts**, so a pixelfont with the pixels being either `color` or `transparent`
- no more colors
- just one
- so
- i made *multiple* bitmap fonts (currently 8, there are 8 fonts in the directory)
- and displayed them all on top of each other
- (initially 256 times, one for each shade of red, but the grub on my VM lagged hard when i did that lmao)
### how
- I didnt even have the doom font as a font, but only as a png
- I exported each letter as their own png
- I used python (i dont even know why) to read every pixel
  - if it was transparent, i would put a 0 for that pixel for that character for all fonts (one font for each shade of gray)
  - if it has a color x, i would put a 1 for that pixel for that character in the font x (and a zero everywhere else)
  - i put more than one gray value in one font to have lesser fonts
- yea, basically it, but i built that pf2 font file byte by byte which was cool, but also a pain, because the docs were meh (and im dumb) and i used python (well, my fault)
### why
- someone put this idea in my head, and i didn't even play a single doom
- but the challenge was to have shaded font in grub, which only can bitmap fonts

## Notes
- the console is black, because gnu knows why
- type (blindly) `loadfont unicode` press `ESC` then `c` again, if it's still black, sorry, try out that other theme i made lol: https://github.com/Lxtharia/minegrub-theme
- **If you add new fonts, you need to `grub-mkconfig ...` again, or else the fonts won't be loaded and your pc will implode** (this sentence may contain missinformation)
