:h buffer => help menu on buffers

buffers => contians text of the file you are editing. Not the file itself.
window => something that displays a buffer
	these can be closed but the uderlying buffer can remain in memory
tabs => are like vviewports, can have many windows or splits open per tab
splits => splits into n windows to view display windows
 like :new will create  a new horizontal split
		:vnew will create a vertical split

RTFM => Read the freindly manual

:h motion => anytime the cursor moves this happens

":" starts anything with this means its a command

Ctrl + a => < C a > Enter => < CR > 

:q! force quit w/o saving
:wq save and quit

hjkl => for movements
x => will delete under the cursor i.e delete in the keyboard
zz => recenter your screen to fit more code around the cursor
w => skip by words end (word over the line)
b => reverse of w, skip words to beginning
dd => delete the whole line
Shift + d => delete from the ccursor to the end of the line
u => undo action
Shift v + d => select the whole line and delete it.
yyp => yank (copy) and paste below
yyP => yank and paste above

Visual mode
Shift v also puts it into visual mode. Shows up as highlighted text
can use the navigation buttons to highlihgt stuff
v to again remove out of visual mode
Visual line mode
Shift v => this will act as the same as above but will select whole lines instead of the characters

Can select lines and "y" will casue it to be yanked and the hit "p" to paste it. Cap p to paste it above as seen already.

Visual mode + d causes it to delete it. Here it yanks it too.
p pastes it right then after but Shift p will also paste it above

:reg => keeps track of all the things you delete and yank as well.
opens in a horizontal split as well
esc esc to leave this above thing.

=> something about registers, yank,delete and paste

Insert mode
i => insert to the left side of the cursor
a => append to the right side of the cursor
Shift i => insert at the beginning of the line
Shift a => append to the end of the line, even takes into account the trailing spaces
o => Put into insert mode in the next line with indents preserved
Shift o => put into insert mode above the current line

:SET
:set scroll and hit tab can show you options
:set scrolloff=8 => will scroll down 8 lines as you approach the bottom or top
:set number => line numbers
	nonumber => to remove
:set relativenumber => relative to your cursor, line numbers are shown .norelativenumber to remove it

=> can go to visual mode v and press line number you want to go to and either j to downside number ref or k to upside number ref and viola its selected until there.

VIMRC => So that these configs stay even when you quit.
and in .vimrc
	set scrolloff
	set number
	set relativenumber 
can do this and save this and these settings get applied to all your vim editors.

similarly => tabstops=4 shiftwidth=4 expandtab smartindent
anything you dont know do :h and the term to serach for

:colorscheme => tab or ctrl + d would help with the options

DIR NAV
vim . => opens the whole dir into vim thingy
NetRW is a plugin for this in VIM
Enter to open the file in VIM
:Ex => explore view opens a new bbuffer of the same folder
:Vex => vertical explore to open the dir in the side
:Sex => split explore to do the horizontal thing split

:q => to close it

Ctrl + w => window mode.
Ctrl + w + s => splits the same code horizontally
ctrl + w + v => splits the same window vertically
ctrl + w then can also use hjkl to move between these windows.
ctrl + w + o => leaves the current buffer open and closes the rest of the windows.

gg=> top of the document
Shift + g => End of the document
:n => goes to nth line

REMAPS
Can remaps your certain key combos to do things like instead of :Vex you can remap it to < space > pv (project view)
`let mapleader = " "`
`nnoremap <leader>pv :Vex<CR>` => `n` for normal mode, `nore` for non repetitve, `map` `<leader>pv` map this space (leader in our case)pv to `:Vex` => Vertical explorer.

EDIT MODE
:e tab would bring up the files listed in the dir and then we can pick the file that is needed directly in edit mode.

There is also a fuzzy finder plugin that ccan list the files and can search throough them and also provides a good preview of the contents of the file. => telescope.nvim

MARKS
Can set global level bookmarks to sepcific places in the code, or window level bookmarsk too.
`m` to enter into bookmark mode. 
`Capital-letters` for global and `small-letters`for local bookmarks
'A => would jump to where A was set globally
'c => would jump to where c was set locally in the window.

ALTERNATE FILES
`%` => points to your current file
`#` => points to the previous file
`Ctrl + ^` => goes back to the previous file. Say in a file and need to go back to nav. this can be used.

JUMPS
`Ctrl + i` => go forward
`Ctrl + o` => go back

PLUGINS
google `vim plug` the one by junegunn
same concept of vscode plugins. have some extension that looks a certain way so that vscode can do its magic,

`iwr -useb https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim | ni $HOME/vimfiles/autoload/plug.vim -Force`
 Did something here, from this it probably autosources it => Directory: C:\\Users\\aadhi\\vimfiles\\autoload

in your .vimrc
`call plug#begin('~/.vim/plugged')`
`call plug#end()`

fzf => fuzzy finder plugin
`:PlugInstall` to install the plugins.

Then use the commands that comes in wtih this plugin and remap them to whatever keys you want to use using map offcourse.

SEARCH usign grep
`:grep "item-to-search" **/*.c` => search something in all files with `.c` extension
`:copen` => shows list of all files
`:cprev` `cnext` => to navigate between this search result.

can again remap these keys to our convinence. 
say `Cj :cprev` and `Ck :cnext` and now can walk to and fro between these serached files

LUA an extension language to build plugins?

SEARCH AND REPLACE
`/` to find something in the file.
`/error` to find `error` in the files.
`n` and `Shift n` to walk back and from the serach result
can use regex also here.
`:set hls ic` => will highlight the `/search-term` you're looking for. `:nohls` to remove highlight

`s/serach-term/replace-with`
`%s/search/replace` => does this for the whole file
can do the same over selected range as well.
`s/search/replace/g` => replaces all instance
`/gc` => will replace all but with prompts

MARCO
`q` starts and stops the macro the macro
`@a` does the macro. `10@a` will repeat the macro 10 times.

`_` => goes to the non first whitespace character of the line
`dt"` => deletes up until the quotes
`f"` => hops to the next quote or any character instead of quotes given
`Shift +f charcter` => goes back to the character

=> `:reg` will contain this macro in the `:a` tag under it.

REGISTER
key value store.
some are filled for us like `y` `d` and other
start with `"` and can take this and edit it our way we ilke and then again addd this into the register
`"by` => this will yank your thing you selected into the `b` register
`"bp` => to edit this register and again yank it to copy it into the registter
This way macros can be re written if something goes wrong while recording the macro.

`5j` goes 5 lines up
`2dd` deletes 2 lines
`2dj` deletes 2 lines up
`dG` delete from cursor to the end of the file

`cc` => delete line and go into insert mode
`c4j` would delete 4 lines down and go into insert mode
`_` beg of the line
`$` end of the line
`D` or `d$` del form cursor till end of the line
`C` or `c$` del and goes into insert mode
`S` del whole line and insert mode and respect indenting
`x` del character
`s` del character and insert mode
`fT` find T in the line and then `,` `;` to jump front and back
`tT` jump right one before the T
`F`and `T` are the opposites of the above
`ct)` change upto the )

`{` `}` jumps to the next paragrpah. can jump between blocks of code faster.
