---
created: 2025-02-19 00:44
---

# The File Structure:

![[pics/1739915169.png]]

first of all we have the init.lua file inside the root directory which `requires` what is inside the `Base` directory.

```lua
require("Base")
```
## Base Directory:

- inside it we have 3 main files first:
  1. init.lua
  2. remap.lua
  3. set.lua

### init.lua:

pretty self explanatory

```lua
require("Base.remap")
require("Base.set")
require("Base.lazy_init")
require("Base.terminal")
```


### [[remap.lua]]


### [[set.lua]]

### lazy_init.lua

- This is basically from the `lazy` docs, the only different thing that the `setup` method is looking foe the file `plugin` which contains my plugins files, so it would be more organized, robust and easier to modify and understand.

```lua
local lazypath = vim.fn.stdpath("data") .. "/lazy/lazy.nvim"
if not vim.loop.fs_stat(lazypath) then
	local lazyrepo = "https://github.com/folke/lazy.nvim.git"
	vim.fn.system({ "git", "clone", "--filter=blob:none", "--branch=stable", lazyrepo, lazypath })
end ---@diagnostic disable-next-line: undefined-field
vim.opt.rtp:prepend(lazypath)

require("lazy").setup({
	spec = "Base.plugin",
	change_detection = { notify = false },
})
```

### [[terminal.lua]]
