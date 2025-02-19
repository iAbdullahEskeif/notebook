---
created: 2025-02-19
tags:
  - linux
  - configs
  - neovim
---
- In this file I have set all the remaps for neovim, it is heavily inspired by the [primagen neovim config video](https://www.youtube.com/watch?v=w7i4amO_zaE) and [neovim Kickstarter](https://github.com/nvim-lua/kickstart.nvim)

## Basics

- Mapping the leader key.

> [!NOTE] Docs
> The Vim editor global dictionaries |g:| |w:| |b:| |t:| |v:| can be accessed
from Lua conveniently and idiomatically by referencing the `vim.*` Lua tables
described below. In this way you can easily read and modify global Vimscript
variables from Lua.

- and `vim.g` allows you to access a global variable inside of `vimscript` like we can see in the `mapleader` case.
- and here I set my leader key to `space`

```lua
vim.g.mapleader = " "
```

- here we are using the `vim.keymap.set` [[vim.keymap]] to set a new keymap to be able to open [[netrw]]

```lua
vim.keymap.set("n", "<leader>pv", "<cmd>Ex<CR>")
```

- Here <cmd>Example<CR> is how you represent a command.

### Moving Selected lines:
```lua
vim.keymap.set("v", "J", ":m '>+1<CR>gv=gv") -- Moves the selected lines down by one line
vim.keymap.set("v", "K", ":m '<-2<CR>gv=gv") -- Moves the selected lines up by one line
```
### Join lines

```lua
vim.keymap.set("n", "J", "mzJ`z") --- Joins the current line with the next line, keeping the curor in placs
```
- here we are setting a mark using the `m` key and giving it the name z at the current cursor position.
- `J` joins the current line with the next line but it moves the cursor by default to the end of the joined line.
- `\`` is the command to *jump to a mark*
- `z`is what we have set earlier.

### Scrolling half a page and centrering the cursor
```lua
vim.keymap.set("n", "<C-d>", "<C-d>zz") -- up
vim.keymap.set("n", "<C-u>", "<C-u>zz") -- down
```
- here `zz` centers the page.

### Centers the search results

```lua
vim.keymap.set("n", "n", "nzzzv")
vim.keymap.set("n", "N", "Nzzzv")
```

- here `zv` **opens enough folds** to make the current line visible if the search result is inside a folded section of text.


### Pastes and delete the content without yanking the deleted text.

```lua
vim.keymap.set("x", "<leader>p", [["_dP]])

vim.keymap.set({ "n", "v" }, "<leader>d", [["_d]])
```

### Yankes the selected text to the system clipboard

```lua
vim.keymap.set({ "n", "v" }, "<leader>y", [["+y]])
```

### Yankes the entire line to the system clipboard

```lua
vim.keymap.set("n", "<leader>Y", [["+Y]])
```

### Disable Ex Mode

- **Disable `Q` (Ex mode)**: Disables the `Q` key to prevent accidental entry into Ex mode.
```lua
vim.keymap.set("n", "Q", "<nop>")
```
### Quickfix and Location List Navigation

- **Next quickfix item**: Moves to the next item in the quickfix list and centers the cursor.

```lua
vim.keymap.set("n", "<C-k>", "<cmd>cnext<CR>zz") 
```
- **Previous quickfix item**: Moves to the previous item in the quickfix list and centers the cursor.

 ```lua
 vim.keymap.set("n", "<C-j>", "<cmd>cprev<CR>zz")
  ```
  
- **Next location list item**: Moves to the next item in the location list and centers the cursor.

```lua
 vim.keymap.set("n", "<leader>k", "<cmd>lnext<CR>zz")
```

- **Previous location list item**: Moves to the previous item in the location list and centers the cursor.

```lua
vim.keymap.set("n", "<leader>j", "<cmd>lprev<CR>zz")
```



### Search and Replace

- **Search and replace current word**: Opens a search and replace prompt for the word under the cursor.

```lua
    vim.keymap.set("n", "<leader>s", [[:%s/\<<C-r><C-w>\>/<C-r><C-w>/gI<Left><Left><Left>]])
```

### Clear Search Highlight

- **Clear search highlight**: Clears the search highlight when pressing `Esc`.

```lua
    vim.keymap.set("n", "<Esc>", "<cmd>nohlsearch<CR>")
```

### Highlight on Yank

- **Highlight yanked text**: Highlights text briefly after yanking (copying).

```lua
vim.api.nvim_create_autocmd("TextYankPost", {
	desc = "Highlight when yanking (copying) text",
	group = vim.api.nvim_create_augroup("kickstart-highlight-yank", { clear = true }),
	callback = function()
		vim.highlight.on_yank()
	end,
})
```
