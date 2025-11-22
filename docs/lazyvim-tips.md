# LazyVim cheat sheet

<https://lazyvim-ambitious-devs.phillips.codes/course/chapter-1/>
<!-- markdownlint-disable MD033 -->
<!-- markdownlint-disable MD013 -->
## Multiple buffers

- Select buffer right and left: H L
- Select buffer from list: `<leader>,` (close buffer on cursor with C-x)
- Open other files: `<leader><space>`
- Close buffer: `<leader>bd` (`<space>bD` to include the window split it's in)
- Close all buffers to the left: `<leader>bl` (r for right)
- Close all buffers except active: `<space>bo`
- Jump to function in current buffer: `<leader>ss`
- You can pin buffers with `<leader>bp` and delete all non pinned buffers with `<leader>bP` (or use it as close all buffers)
- Open scratch buffer tied to cwd: `<space>.` (`<space>S` for scratch buffers picking list)
Add TODOs in files you want to work on in future but don't need now and
  delete their buffers, git will track them

## Indentation/Format

Plugin: conform.nvim to edit formatting e.g. indent size

- Increase on current line: `>>` (`<<` to decrease)
- Indent on many lines with Visual mode + `<` or `>`
- Increase on blanks-delimited paragraph: `>ap`
- Increase 5 times on current line in visual mode: `v5>`
- Format all in normal: `<leader>cf`
- For indentation only: `gg=G` (jump to start, indent, jump to end of file)

## Inserting

- Insert before current pos: `i` (`I` for before current line)
- Insert after current pos: `a` (`A` for after current line)
- Insert on next line: `o` (`O` for previous line)
- In insert mode, paste from clipboard: `C-r +`

## Moving

- Seek and move to (within screen): `s`
- Find char and move to next or Nth one: `f` (`F` for previous or Nth one)
- Same as Find but move to before char: `t` or `T` (useful with deletes etc)
- Move to end of line: `$` or `End`
- Mode to start of line: `0` or `Home`
- Scroll up half a screen: `Ctrl-u` (`Ctrl-d` for down)
- Move to next word: `w` (`W` for after next whitespace)
- Move to previous word: `b` (`B` for previous whitespaced word)
- Move to end of current word: `e` (`E` before next whitespace)
- Move to line number 10: `:10`
- Move to top of file: `gg` (`G` for end of file)
- Go to previous historical move: `Ctrl-o` (`Ctrl-i` for next)
- Move by sentence/paragraph: `()` / `{}`
- Move to "something": `[]` (Used to jump out of block of code or language stuff. `]%` = jump to end of whatever is bracketing me)
- Jump to other reference to the variable under the cursor: `[[` / `]]` (Chapter 7 for details)

## Etc

- Open LazyVim configs: `<leader>fc`
- Open fuzzy finder in root dir: `<space><space>` (`Tab` to select multiple files) (`<space>fF` for cwd)
- Print working dir: `:pwd`
- Change working dir: `:cd /dir`
- Enable/disable spell check: `<space>us` (`z=` for suggestions)

## Explorer

- Jump from window/file: `<C-h>`
- Open/close explorer in rootdir: `<leader>e` (`E` for cwd)
- Select many for open: `Tab`
- Add file/dir: `a`
- Rename file/dir: `r`
- Yank/put/move/help: `y/p/m/?`
- Open in vertical split: `C-v` (`C-s` for horizontal)

## Editing

- `<count><verb><motion>` or `<verb><count><motion>`
- Insert 50 asterisks: `50i*<esc>`
- Delete: `d` (`D` for del to end of line)
- Change, del+ins: `c` (ex: `cw` to replace a word) (`C` to change to end of line)
- `dd/cc/3dd`: Delete entire line/change entire line/delete 3 lines
- Del button: `x` (`X` for left direction, ex: `5x`)
- Replace one char: `r`
- Join lines: `J`
- Repeat action: `.`
- Undo: `u` (`C-r` for redo)
- Increment/decrement numbers, dates, bools etc with editor.dial plugin: `C-a`/`C-x`
A lot more like objects in chapter 7.

## Copy/paste

- Visual mode: `v`
- Copy entire line: `yy`
- Copy from cursor to end of line: `y`
- Paste: `p` (`P` for paste before)
- In visual mode, go to other end of selection: `o`
- Go to last visual selection: `gv`
- Line-wise visual mode: `V`
- add/remove indentation before put: `>p` `<p` `>p` `<p`

## Windows

- Split vertical: `<space>|` (`<space>-` split horizontal)
- Move cursor between windows: `C-h/j/k/l`
- Delete window: `<space>wd` (`<space>wo` for close all Others)
- Resize: Use mouse

## Tabs

- New tab: `<space><tab><tab>`
- Navigate tabs: `gt` (`gT` for previous)
- Jump to tab 3: `3gt`
- Delete window and the tab will disappear
- Close all windows and the tab: `<space><tab>d`

## Folding

- Collapse/open fold: `za`
- Open all folds: `zR`
- Open folds recursively: `zO`

## Sessions

Sessions are stored in the cwd

- Open session picker: `<space>qS`
- Don't save current as a new latest session: `<space>qd`

## Code

- Go to definition, where the keyword is defined in any file: `gd` (`C-o` to go back after)
- Go to references, where the function/variable etc is used: `gr` (`Alt-r` send all or selected results to Trouble)
- Show help for word or symbol under cursor: `K`
- Search symbol with picker in current file: `<space>ss` (`<space>sS` in current project)
- Select symbols like in explorer: `<space>cs`
- Toggle comment on line: `gcc` (`5gcc` for 5 lines or use Visual with `gc`)

## Search

- Open search highlighting first result after cursor: `/` (Go to with `<enter>`)
- Go to next result: `n` (`N` for previous)
- Search and replace, Grug-far.nvim: `<space>sr`
- Ignore case/regex: <https://lazyvim-ambitious-devs.phillips.codes/course/chapter-12/#_ignore_case>

## Marks

- Set mark on any alphabet key: `m<key>` (Capital for global mark)
- Go to mark: `'<key>` (or use the picker on `'`)
- Delete mark: `:delm <key>`
- Go to last place inserted or changed text: `'.`

## Registers

One register on each keyboard key

- Cut 3 words to register a: `"ad3w`
- Put register a: `"ap`
- Append to register a: `"Ay`
- Open list with registers and their content: `"` (`<leader>s"` for fuzzy finder list with registers)
- Best way to list and select registers with plugin yanky.nvim: `<space>p`
- Cycle put backwards in history: `[y` `p[y[y` puts the third historical yank, delete...

## AI

- Try Codeium mby. `<space>a` for AI menu

## Debugging

## Testing

## Git / Source control

## Mason etc

Some extra packages of some kind related to language

- Open Mason: `<space>cm`
- Open Noice messages: `<space>sn`
- Open LspInfo debugging: `<space>cl`
- First place to check health: `:LazyHealth`
- Second place to check health: `:checkhealth`

## Trouble and Quick fix

- Open menu: `<space>x`
- When standing on a diagnostic, open code action: `<space>ca`
