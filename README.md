# ItziKode
ItziKode is a dark **color scheme for [VIM](https://www.vim.org) / [NeoVIM](https://neovim.io)** heavily inspired by the look of the Dark+ scheme of [Visual Studio Code](https://code.visualstudio.com/). While many of the colors are same, there are additional colors for specific usage or reserved for future use. The scheme also defines specific GUI colors (e.g. popup menu) and fully supports [`vim-airline`](https://github.com/vim-airline/vim-airline).

**:exclamation: To install and enable this colorscheme, [read installation instructions](#installation).**

*This colorscheme does also support 256 and 8/16 color terminals. See [installation instructions](#installation) step 3.*

## Screenshots

### gVim / modern terminals
![Ruby and NERDTree](https://user-images.githubusercontent.com/18270061/162501343-eca44a22-6f36-4846-bf6b-7b0460707597.png)
![Editing HTML and CSS](https://user-images.githubusercontent.com/18270061/162501174-6b08b20d-d7c7-49a3-8b1e-f1ef18905d16.png)

*Code samples [1](http://sandbox.mc.edu/~bennet/ruby/code/), [2](https://tmtheme-editor.herokuapp.com/), [`nerdtree`](https://github.com/scrooloose/nerdtree)*

### Terminals with limited color support

#### Fixed 256 colors
![Terminal on Debian with 256 colors](https://user-images.githubusercontent.com/18270061/162501606-8bbfe078-c0f7-4a42-8d93-ee4de45ed2f6.png)

#### Fixed 8/16 colors
![Terminal on Debian with 16 colors](https://user-images.githubusercontent.com/18270061/162501804-5b975527-7ca5-477f-b269-7c80c0e3b3d7.png)

## Color Palette
![Color Palette](https://user-images.githubusercontent.com/18270061/162502068-648a324b-dbb3-45a5-8f19-fc19c6cb6179.png)

## Installation

### 1) Download

Simply as any other VIM plugins: download manually or follow the standard procedure of your plugin manager:
*  [Vundle](https://github.com/gmarik/vundle)
 ```
 Plugin 'IzhakJakov/ItziKode'
 ```
*  [vim-plug](https://github.com/junegunn/vim-plug)
```
Plug 'IzhakJakov/ItziKode'
```
*  manual

   copy all of the files to `~/.vim` (or `$HOME\vimfiles` on Windows) directory

### 2) Enable in `.vimrc`, `init.vim`, etc.

Add the following line:

```
colorscheme itzikode
```

If you have [`vim-airline`](https://github.com/vim-airline/vim-airline), you can also enable the provided theme:

```
let g:airline_theme = 'itzikode'
```

### 3) Terminal support

#### 3.1) If you use gVim or NeoVIM with a modern terminal
:+1: The colorscheme should work out of the box. No need to setup anything else!

#### 3.2) If the colors seem to be wrong
If your terminal supports 256 colors (see [this script](http://www.robmeerman.co.uk/unix/256colours) if you want to test your terminal), you **may need to set `t_Co` to 256** and [possibly also reset the `t_ut` value](http://vi.stackexchange.com/questions/238/tmux-is-changing-part-of-the-background-in-vim) in your `.vimrc`, `init.vim`, etc. before setting the colorscheme:

```
set t_Co=256
set t_ut=
colorscheme itzikode
```

(Additionally, if you don't want to or cannot use `t_Co`, you can `let g:itzikode_term256=1`.)

#### 3.3) If your terminal support rendering italic fonts
Italics in comments can be enabled by setting `g:itzikode_italics = 1` _before_
setting the colorscheme, like so:
```
let g:itzikode_italics = 1
colorscheme itzikode
```

#### 3.4) If your terminal only supports 8/16 colors

:exclamation: Before following those steps, first try step (**3.2**) - maybe your terminal does support 256 colors!

If your terminal does not support 256 colors, you may want to change your terminal colors:

##### 3.4.1) Some Unix terminals
Clone [`base16-shell`](https://github.com/chriskempson/base16-shell/) into `~/.config/base16-shell`:

```
git clone https://github.com/chriskempson/base16-shell.git ~/.config/base16-shell
```

Then copy a script from this (`ItziKode`) repository (`base16/templates/shell/scripts/base16-itzikode.sh`) into `~/.config/base16-shell/scripts`.

Following the instructions from [`base16-shell`](https://github.com/chriskempson/base16-shell/), you should now modify your `~/.bashrc` or `~/.zshrc` (depending on your shell) and insert the following lines:

```
BASE16_SHELL=$HOME/.config/base16-shell/
[ -n "$PS1" ] && [ -s $BASE16_SHELL/profile_helper.sh ] && eval "$($BASE16_SHELL/profile_helper.sh)"
```

Now start a new shell and type the following command: `base16_itzikode`.

You should now be able to use Vim with your new colorscheme.

##### 3.4.2) iTerm2
iTerm2 should actually support 256 colors, try setting `Report Terminal Type` to `xterm-256color` and follow step 3.2). If it does not work, you can manually modify your terminal colors in settings (`CMD+i`, Colors tab) following the [color palette picture](#color-palette). You will have to choose which color to use as red, blue etc. according to your personal preferences.

##### 3.4.3) PuTTY
PuTTY should actually support 256 colors, try following [steps on StackOverflow](http://superuser.com/questions/436910/emulate-256-colors-in-putty-terminal). If it does not work, run `base16/templates/putty/putty/base16-itzikode.reg` to modify your registry, then run PuTTY and load `itzikode` in the session list. This will modify your PuTTY terminal colors.

## FAQ

### The background color in my terminal is wrong when there is no text!
Try resetting the `t_ut` value in your `.vimrc`, `init.vim`, etc. as [described here](http://vi.stackexchange.com/questions/238/tmux-is-changing-part-of-the-background-in-vim):
```
set t_Co=256
set t_ut=
colorscheme itzikode
```

### What is and how to enable the conservative mode?
If you don't like many colors and prefer the **conservative style of the standard Visual Studio**, you can try the conservative mode with reduced number of colors. To enable it, put the following line to your `.vimrc` *before* setting the scheme, like so:

```
let g:itzikode_conservative = 1
colorscheme itzikode
```

### Something is broken but I know how to fix it!
Pull requests are welcome! Feel free to send one with an explanation!

### Why does file syntax not look exactly like in Visual Studio Code?
Because Vim uses different syntax rules. This is just a colorscheme for vim, not a syntax definition.

### My favourite language has wrong / bad / awful colors!
There are a lot of syntax definitions with different highlight groups. Feel free to send a pull request with additional highlight groups!

### What setup can I see on the first screenshots?
Screenshots come from gVim on Windows with the following font options and [`vim-airline`](https://github.com/vim-airline/vim-airline) enabled.

```
set enc=utf-8
set guifont=Powerline_Consolas:h11
set renderoptions=type:directx,gamma:1.5,contrast:0.5,geom:1,renmode:5,taamode:1,level:0.5
```
