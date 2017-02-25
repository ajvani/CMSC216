#Purpose
I made this repository basically to hold my CMSC216 class notes, but I guess I can share my vim configuration as well. 
#Vim
##Making it work
###Setup
```
$ git clone https://github.com/ajvani/CMSC216.git &&\
rm -rf ~/.vimrc ~/.vim && cp -rf ~/CMSC216/vim ~/.vim\
&& cp ~/.vim/vimrc ~/.vimrc && rm -rf ~/CMSC216 ./.vim/vimrc
```

###Basic Vim Instructions
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

##Features
###Initial Note
- Unfortunately grace only has Vim 7, so I tried my best to make this work really well
- If you do not like any of the following that are marked "PLUGIN", you can remove them by running the following command: 
```
$ rm -rf ~/.vim/bundle/<plugin_name>
```

###File Management
- While in vim (not in insert of visual mode) `<Ctrl-N>` toggles the file explorer
- Use up/down or k/j to move up and down through the files and press `<Ent>` to open a file
- Opening a file does not "close out" of another file, but creates a buffer
- Use `<Ctrl-O>` and `<Ctrl-P>` to move between buffers, and `<q>` to quit out of a buffer

###Color Theme(PLUGIN)
- I use vim-colors-solarized as my theme. This theme won't work well with terminal because of default color configuration. 
- I use iterm and use their solarized theme, so it looks really nice for me.
- If you dont want to use iterm here are a few options: 
    + Download a solarized theme for Mac Terminal ([here](https://github.com/tomislav/osx-terminal.app-colors-solarized) is one that works)
        * NOTE: I don't really like this because it messes up the syntax colors, but up to you. 
    + Remove or comment out these lines in .vimrc (REMOVES SOLARIZED SYNTAX HIGHLIGHTING FROM VIM):
``` 
        let g:solarize_termcolors=256
        set background=dark
        colorscheme solarized
```

    + Edit every single color in the terminal settings to match the solarized color format. (Pls don't do this, it's a waste of time)
- If you want a different color theme, you can find a different one and git clone it into `~/.vim/bundle`

###Accelerated Smooth Scroll(PLUGIN)
- Basically this just scrolls through your file real fast. Use `<Ctrl-U>/<Ctrl-B` for scroll up and `<Ctrl-D>/<Ctrl-F>` for scroll down
- Official github repo: https://github.com/yonchu/accelerated-smooth-scroll

###Autopairs(PLUGIN)
- I wouldn't remove this because it autocompletes your parenthesis/braces/etc. It's nice. 
- Official github repo: https://github.com/jiangmiao/auto-pairs

###Buftabline(PLUGIN)
- This the tabs up top that show your buffers.
- Official github repo: https://github.com/ap/vim-buftabline

###Lightline(PLUGIN)
- This is the status line at the bottom which looks better than the traditional one
- Official github repo: https://github.com/itchyny/lightline.vim
