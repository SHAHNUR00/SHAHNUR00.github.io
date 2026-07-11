# Neovim Cheat Sheet — VSCode Operations Mapped to Neovim

A practical reference mapping common VSCode actions to their Neovim equivalents.

---

## File & Buffer Management

| VSCode Action | Neovim Command |
|---|---|
| Open file (Ctrl+O) | `:e path/to/file` |
| New file | `:e newfile.txt` |
| Save (Ctrl+S) | `:w` |
| Save As | `:w newname.txt` |
| Save All | `:wa` |
| Close file (Ctrl+W) | `:bd` (buffer delete) |
| Close without saving | `:bd!` |
| Quit editor | `:q` |
| Quit without saving | `:q!` |
| Save and quit | `:wq` or `:x` |
| Save & quit all | `:wqa` |
| Switch between open files | `:bnext` / `:bprev` or `<leader>bn` / `<leader>bp` (if mapped) |
| List open buffers | `:ls` or `:buffers` |
| Jump to buffer N | `:b N` |
| Reopen closed file | Nvim has no native "recently closed" — use `:oldfiles` then `:e #<N` |
| File Explorer (Ctrl+Shift+E) | `:Ex` (netrw) or `:NvimTreeToggle` (with nvim-tree) |

---

## Navigation

| VSCode Action | Neovim Command |
|---|---|
| Go to line (Ctrl+G) | `:N` (e.g. `:42`) or `NG` (e.g. `42G`) |
| Go to file start/end | `gg` / `G` |
| Go to matching bracket | `%` |
| Go to definition (F12) | `gd` (with LSP) |
| Go to references | `gr` (with LSP) |
| Peek definition | `K` (hover) or `gd` in split |
| Go back / forward | `Ctrl+o` / `Ctrl+i` (jump list) |
| Next/Prev word | `w` / `b` |
| Next/Prev WORD (space-separated) | `W` / `B` |
| End of word | `e` |
| Start/End of line | `0` / `$` |
| First non-blank char of line | `^` |
| Scroll down/up half page | `Ctrl+d` / `Ctrl+u` |
| Scroll down/up full page | `Ctrl+f` / `Ctrl+b` |
| Go to top/middle/bottom of screen | `H` / `M` / `L` |
| Jump to next/prev paragraph | `}` / `{` |
| Go to next/prev function (with treesitter) | `]]` / `[[` (customizable) |

---

## Multi-cursor / Selection (VSCode's Ctrl+D, Alt+Click)

Neovim doesn't have native multi-cursor like VSCode — closest equivalents:

| VSCode Action | Neovim Equivalent |
|---|---|
| Select next occurrence (Ctrl+D) | Use `*` to search word under cursor, then `cgn` to change next match, `.` to repeat |
| Select all occurrences (Ctrl+Shift+L) | `:%s/word/replacement/g` (substitute) |
| Multi-cursor column edit | Visual Block mode: `Ctrl+v`, select column, `I` to insert, `Esc` to apply to all lines |
| Add cursor above/below (Alt+Click) | Visual Block mode (`Ctrl+v`) + `I`/`A` for insert/append |
| True multi-cursor plugin | Install `vim-visual-multi` for VSCode-like Ctrl+D behavior |

---

## Editing

| VSCode Action | Neovim Command |
|---|---|
| Undo (Ctrl+Z) | `u` |
| Redo (Ctrl+Y) | `Ctrl+r` |
| Cut line (Ctrl+X) | `dd` |
| Copy line (Ctrl+C) | `yy` |
| Paste (Ctrl+V) | `p` (after cursor) / `P` (before cursor) |
| Duplicate line (Shift+Alt+Down) | `yyp` |
| Move line down/up (Alt+Down/Up) | `:m .+1` / `:m .-2` (or map `Alt+j`/`Alt+k`) |
| Delete word | `dw` |
| Delete to end of line | `D` or `d$` |
| Delete char (Delete key) | `x` |
| Delete char before cursor (Backspace) | `X` |
| Change word (select+type over) | `cw` |
| Change entire line | `cc` or `S` |
| Indent line (Tab) | `>>` |
| Outdent line (Shift+Tab) | `<<` |
| Indent selection | Visual select, then `>` |
| Comment line (Ctrl+/) | `gcc` (with Comment.nvim plugin) |
| Comment selection | Visual select, then `gc` |
| Toggle case | `~` (single char) or `g~~` (line) |
| Uppercase/lowercase selection | `gU` / `gu` in visual mode |
| Join lines (no VSCode equivalent shortcut) | `J` |
| Insert mode (start typing) | `i` (before cursor) / `a` (after cursor) |
| Insert at line start/end | `I` / `A` |
| New line below/above (Enter) | `o` / `O` |
| Replace single character | `r` + char |
| Replace mode (overtype) | `R` |

---

## Find & Replace

| VSCode Action | Neovim Command |
|---|---|
| Find (Ctrl+F) | `/pattern` (forward) or `?pattern` (backward) |
| Find next/prev (F3/Shift+F3) | `n` / `N` |
| Find word under cursor | `*` (forward) / `#` (backward) |
| Replace (Ctrl+H) | `:s/old/new/` (current line) |
| Replace all in file (Ctrl+Shift+H) | `:%s/old/new/g` |
| Replace with confirmation | `:%s/old/new/gc` |
| Replace in selection only | Visual select, then `:s/old/new/g` |
| Find in files (Ctrl+Shift+F) | `:grep pattern` (needs grepprg set) or use Telescope: `:Telescope live_grep` |
| Case-insensitive search | Add `\c` in pattern, e.g. `/pattern\c`, or `:set ignorecase` |

---

## Selection

| VSCode Action | Neovim Command |
|---|---|
| Select all (Ctrl+A) | `ggVG` |
| Select line (click on gutter) | `V` |
| Select word | `viw` |
| Select inside quotes/brackets | `vi"` / `vi(` / `vi{` |
| Select around quotes/brackets (includes them) | `va"` / `va(` / `va{` |
| Extend selection | `v` then movement keys |
| Block/column selection | `Ctrl+v` |
| Select paragraph | `vip` |

---

## Split Windows / Panes

| VSCode Action | Neovim Command |
|---|---|
| Split editor right | `:vsplit` or `:vs` |
| Split editor down | `:split` or `:sp` |
| Switch between splits | `Ctrl+w` then `h/j/k/l` |
| Close current split | `Ctrl+w c` or `:close` |
| Close all but current split | `Ctrl+w o` or `:only` |
| Resize split | `Ctrl+w +` / `Ctrl+w -` (height), `Ctrl+w <` / `Ctrl+w >` (width) |
| Equalize split sizes | `Ctrl+w =` |
| Move split to new tab | `Ctrl+w T` |

---

## Tabs

| VSCode Action | Neovim Command |
|---|---|
| New tab | `:tabnew` |
| Next/Prev tab (Ctrl+Tab / Ctrl+Shift+Tab) | `gt` / `gT` |
| Go to tab N | `N gt` (e.g. `2gt`) |
| Close tab | `:tabclose` |
| Close all other tabs | `:tabonly` |

---

## Terminal

| VSCode Action | Neovim Command |
|---|---|
| Open terminal (Ctrl+`) | `:terminal` or `:term` |
| Open terminal in split | `:vsplit \| terminal` |
| Exit terminal insert mode | `Ctrl+\` then `Ctrl+n` |
| Toggle terminal (with toggleterm.nvim) | Custom keymap, e.g. `<C-\>` |

---

## Code Intelligence (LSP — requires nvim-lspconfig + servers installed)

| VSCode Action | Neovim Command |
|---|---|
| Go to Definition (F12) | `gd` |
| Go to Declaration | `gD` |
| Find All References (Shift+F12) | `gr` |
| Hover / Show Docs | `K` |
| Rename Symbol (F2) | `<leader>rn` (via `vim.lsp.buf.rename()`) |
| Quick Fix (Ctrl+.) | `<leader>ca` (via `vim.lsp.buf.code_action()`) |
| Format Document (Shift+Alt+F) | `<leader>f` (via `vim.lsp.buf.format()`) or `gq` for basic formatting |
| Go to next/prev error (F8/Shift+F8) | `]d` / `[d` (diagnostics) |
| Show error/problem details | `:lua vim.diagnostic.open_float()` (often mapped to `<leader>e`) |
| Problems panel (Ctrl+Shift+M) | `:Telescope diagnostics` or `:lua vim.diagnostic.setloclist()` |
| Signature help | `Ctrl+k` in insert mode (via LSP) |
| Autocomplete (Ctrl+Space) | Automatic with `nvim-cmp`, or `Ctrl+n`/`Ctrl+p` for built-in omni-completion |

---

## Fuzzy Finder / Command Palette

| VSCode Action | Neovim Command (with Telescope.nvim) |
|---|---|
| Command Palette (Ctrl+Shift+P) | `:Telescope commands` |
| Quick Open file (Ctrl+P) | `:Telescope find_files` |
| Search symbols in file (Ctrl+Shift+O) | `:Telescope lsp_document_symbols` |
| Search symbols in workspace | `:Telescope lsp_workspace_symbols` |
| Go to recent files | `:Telescope oldfiles` |

---

## Git Integration (with gitsigns.nvim / fugitive.vim)

| VSCode Action | Neovim Command |
|---|---|
| Source Control panel | `:Git` (with vim-fugitive) |
| Stage changes | `:Git add %` or `:Git add .` |
| Commit | `:Git commit` |
| View diff | `:Gdiffsplit` (fugitive) or `:Gitsigns preview_hunk` |
| View blame | `:Git blame` |
| Next/Prev change (hunk) | `]c` / `[c` (with gitsigns) |
| Stage hunk | `<leader>hs` (gitsigns default-style mapping) |

---

## Folding (Code Folding — Ctrl+Shift+[ / ])

| VSCode Action | Neovim Command |
|---|---|
| Fold current block | `za` (toggle) or `zc` (close) |
| Unfold | `zo` |
| Fold all | `zM` |
| Unfold all | `zR` |
| Fold level N | `zN` (e.g. `z2`) |

---

## Copy/Move Line Ranges (Ex Commands)

No direct VSCode equivalent — these let you copy or move a range of lines to another location in a single command, without separate yank + paste.

| Action | Neovim Command |
|---|---|
| Copy lines 10-20 to after current line | `:10,20t.` |
| Copy lines 10-20 to after line 30 | `:10,20t30` |
| Copy lines 10-20 to end of file | `:10,20t$` |
| Copy lines 10-20 to before current line | `:10,20t.-1` |
| Copy lines 10-20 to top of file | `:10,20t0` |
| Move (cut-paste) lines 10-20 to after current line | `:10,20m.` |
| Move lines 10-20 to after line 30 | `:10,20m30` |
| Move lines 10-20 to end of file | `:10,20m$` |
| Move lines 10-20 to top of file | `:10,20m0` |

Notes:
- `t` = `:copy` (duplicates the range)
- `m` = `:move` (relocates the range, removing it from the original spot)
- `.` refers to the current cursor line, so the range is inserted immediately after it
- These work great for reordering functions, moving code blocks, or duplicating chunks of boilerplate

---

## Marks & Macros (No direct VSCode equivalent, but powerful)

| Action | Neovim Command |
|---|---|
| Set a mark | `m` + letter (e.g. `ma`) |
| Jump to mark | `` ` `` + letter (e.g. `` `a ``) |
| Record macro | `q` + register letter, do actions, `q` to stop |
| Play macro | `@` + register letter |
| Repeat last macro | `@@` |
| Repeat last change | `.` |

---

## Misc

| VSCode Action | Neovim Command |
|---|---|
| Zen mode / distraction free | `:only` + custom plugin (e.g. zen-mode.nvim) |
| Minimap | Plugin needed (e.g. codewindow.nvim) |
| Settings (Ctrl+,) | Edit `init.lua` directly |
| Extensions/Plugins panel | `:Lazy` (if using lazy.nvim) or `:PackerStatus` (packer.nvim) |
| Check for LSP/tool issues | `:checkhealth` |
| Install LSP servers | `:Mason` |

---

## Quick Notes for Your Setup

- Since you use **Mason** for LSP (clangd, html-lsp, css-lsp, typescript-language-server), remember `:Mason` opens the manager UI and `:LspInfo` shows what's attached to the current buffer.
- Since tree-sitter parsers are separate from LSP, use `:TSInstall <lang>` and `:TSUpdate` for syntax highlighting/parsing.
- For your CP (C++) workflow, a `compile_flags.txt` in your project root (e.g. `-std=c++17`) helps clangd give accurate diagnostics.
