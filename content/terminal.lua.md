---
created: 2025-02-19
---

### **1. Local Settings for Terminal Buffers**

```lua
local set = vim.opt_local

-- Set local settings for terminal buffers
vim.api.nvim_create_autocmd("TermOpen", {
	group = vim.api.nvim_create_augroup("custom-term-open", {}),
	callback = function()
		set.number = false
		set.relativenumber = false
		set.scrolloff = 0
	end,
})
```


#### **What it does:**

- **`local set = vim.opt_local`**  
    Creates a shorthand for `vim.opt_local`, which is used to set buffer-local options.
    
- **`vim.api.nvim_create_autocmd("TermOpen", { ... })`**  
    Creates an autocommand that triggers when a terminal buffer is opened.
    
- **`group = vim.api.nvim_create_augroup("custom-term-open", {})`**  
    Creates an autocommand group named `custom-term-open` to manage related autocommands.
    
- **`callback = function() ... end`**  
    Defines the behavior when the `TermOpen` event is triggered:
    
    - **`set.number = false`**  
        Disables line numbers in the terminal buffer.
        
    - **`set.relativenumber = false`**  
        Disables relative line numbers in the terminal buffer.
        
    - **`set.scrolloff = 0`**  
        Sets the `scrolloff` (number of lines to keep above/below the cursor) to 0 for the terminal buffer.
        

#### **Why it's useful:**

- Terminal buffers don’t need line numbers or relative line numbers, as they are primarily used for interactive commands.
    
- Disabling these features keeps the terminal interface clean and focused.
    

---

### **2. Easily Exit Terminal Mode**

```lua
-- Easily hit escape in terminal mode.
vim.keymap.set("t", "<esc><esc>", "<c-\\><c-n>")
```


#### **What it does:**

- **`vim.keymap.set("t", "<esc><esc>", "<c-\\><c-n>")`**  
    Creates a key mapping in terminal mode (`t`):
    
    - **`<esc><esc>`**: Pressing `Esc` twice.
        
    - **`<c-\\><c-n>`**: Sends the key sequence `Ctrl+\` followed by `Ctrl+n`, which exits terminal mode and returns to Normal mode.
        

#### **Why it's useful:**

- In Neovim, you need to press `Ctrl+\` followed by `Ctrl+n` to exit terminal mode. This mapping makes it easier to exit by simply pressing `Esc` twice.
    

---

### **3. Open a Terminal at the Bottom of the Screen**

```lua
-- Open a terminal at the bottom of the screen with a fixed height.
vim.keymap.set("n", ",st", function()
	vim.cmd.new()
	vim.cmd.wincmd "J"
	vim.api.nvim_win_set_height(0, 12)
	vim.wo.winfixheight = true
	vim.cmd.term()
end)
```

#### **What it does:**

- **`vim.keymap.set("n", ",st", function() ... end)`**  
    Creates a key mapping in Normal mode (`n`):
    
    - **`,st`**: The key sequence to trigger the mapping.
        
    - **`function() ... end`**: The action to perform when the mapping is triggered.
        
- **`vim.cmd.new()`**  
    Opens a new buffer.
    
- **`vim.cmd.wincmd "J"`**  
    Moves the current window to the bottom of the screen.
    
- **`vim.api.nvim_win_set_height(0, 12)`**  
    Sets the height of the current window to 12 lines.
    
- **`vim.wo.winfixheight = true`**  
    Makes the window height fixed, preventing it from being resized.
    
- **`vim.cmd.term()`**  
    Opens a terminal in the current buffer.
    

#### **Why it's useful:**

- This mapping provides a quick way to open a terminal at the bottom of the screen with a fixed height, which is convenient for running commands without disrupting your workflow.
