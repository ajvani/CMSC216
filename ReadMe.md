# Purpose
I made this repository basically to hold my CMSC216 class notes, but I guess I can share my vim configuration as well. 
# Vim
## Making it work
### Setup
Copy paste this: 

```
$ cd ~/ && git clone --recurse-submodules https://github.com/ajvani/CMSC216.git\
&& rm -rf ~/.vimrc ~/.vim && cp -rf ~/CMSC216/vim ~/.vim\
&& cp ~/.vim/vimrc ~/.vimrc && rm -rf ~/CMSC216 ~/.vim/vimrc
```

### Basic Vim Instructions
Don't know vim? Here's a basic instructional
- `:q` = quit (can't quit edited file without saving)
- `:w` = save
- `:wq` = save & quit
- `:q!` = quit & don't save
- `i` = enters insert mode
- `v` = enters visual mode
- `esc` = exits whatever mode you're in
- `h,j,k,l` = move left, down, up, right respectively
- `o` = adds a line under your current line and enters insert mode

## Features
### Initial Note
- Unfortunately grace only has Vim 7, so I tried my best to make this work really well
- If you do not like any of the following that are marked "PLUGIN", you can remove them by running the following command: 
```
$ rm -rf ~/.vim/bundle/<plugin_name>
```

### File Management
- While in vim (not in insert of visual mode) `<Ctrl-N>` toggles the file explorer
- Use up/down or k/j to move up and down through the files and press `<Ent>` to open a file
- Opening a file does not "close out" of another file, but creates a buffer
- Use `<Ctrl-O>` and `<Ctrl-P>` to move between buffers, and `<q>` to quit out of a buffer

### Color Theme(PLUGIN)
- I use vim-colors-solarized as my theme
    + I give instructions for Solarized Dark, you can use light if you prefer a lighter theme, just replace every 'dark' with 'light' and replace `set background=dark` with `set background=light` in ~/.vimrc
- This theme does not look good by default
- Options (For PC)
    + If you use MobaXterm do this: 
        * Settings > Configuration > Terminal > Default colors scheme: "Solarized dark"
- Options (For UNIX)
    + Download iterm2
        * Preferences > Profiles > Colors > Color Presets: Solarized Dark
    + Download a solarized theme for Mac Terminal ([here](https://github.com/tomislav/osx-terminal.app-colors-solarized) is one that works)
        * NOTE: I don't really like this because the syntax coloring is a little off, but up to you. 
    + Just don't use solarized theme:
        * Remove following lines from ~/.vimrc 

        ``` 
        let g:solarize_termcolors=256
        set background=dark
        colorscheme solarized
        ```

        * Run `$ rm -rf ~/.vim/bundle/vim-colors-solarized`
    + Edit every single color in the terminal settings to match the solarized color format. (Pls don't do this, it's a waste of time)
- If you want a different color theme, you can find a different one and git clone it into `~/.vim/bundle`
- Official github repo: https://github.com/altercation/vim-colors-solarized

### Accelerated Smooth Scroll(PLUGIN)
- Basically this just scrolls through your file real fast. Use `<Ctrl-U>/<Ctrl-B` for scroll up and `<Ctrl-D>/<Ctrl-F>` for scroll down
- Official github repo: https://github.com/yonchu/accelerated-smooth-scroll

### Autopairs(PLUGIN)
- I wouldn't remove this because it autocompletes your parenthesis/braces/etc. It's nice. 
- Official github repo: https://github.com/jiangmiao/auto-pairs

### Buftabline(PLUGIN)
- This the tabs up top that show your buffers.
- Official github repo: https://github.com/ap/vim-buftabline

### Lightline(PLUGIN)
- This is the status line at the bottom which looks better than the traditional one
- Official github repo: https://github.com/itchyny/lightline.vim
