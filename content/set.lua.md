---
created: 2025-02-19
---
### **General Settings**

1. **`vim.g.have_nerd_font = true`**
    Enables the use of Nerd Fonts in the editor. Nerd Fonts are patched fonts that include a large number of glyphs, which are useful for displaying icons and symbols in the editor.

2. **`vim.opt.number = true`**
    Enables line numbers in the left-hand margin of the editor.

3. **`vim.g.netrw_browsex_viewer = "-"`**
    Disables the default viewer for `netrw` (a file explorer in Vim). The `"-"` value means no external viewer is used.

4. **`vim.g.netrw_banner = 0`**
    Hides the banner in the `netrw` file explorer for a cleaner interface.

5. **`vim.opt.showmode = true`**
    Displays the current mode (e.g., INSERT, VISUAL, NORMAL) in the status line.


6. **`vim.opt.breakindent = true`**
    Ensures that when a line is wrapped, the continuation lines are indented to match the start of the line.

7. **`vim.opt.ignorecase = true`**
    Makes search operations case-insensitive.

8. **`vim.opt.smartcase = true`**
    Overrides `ignorecase` if the search pattern contains uppercase letters, making the search case-sensitive in such cases.

9. **`vim.opt.signcolumn = "yes"`**
    Always shows the sign column (used for displaying signs like breakpoints, Git changes, etc.) to avoid UI shifting.

10. **`vim.opt.updatetime = 250`**
    Sets the time (in milliseconds) before the `CursorHold` event is triggered. Useful for plugins like LSP or diagnostics.

11. **`vim.opt.timeoutlen = 300`**
    Sets the time (in milliseconds) to wait for a mapped sequence to complete.

12. **`vim.opt.splitright = true`**
    Makes new vertical splits open to the right of the current window.

13. **`vim.opt.splitbelow = true`**
    Makes new horizontal splits open below the current window.

14. **`vim.opt.list = true`**
    Displays invisible characters (e.g., tabs, spaces) as defined by `listchars`.

15. **`vim.opt.colorcolumn = "40"`**
    Highlights the 40th column to serve as a visual guide for line length.

16. **`vim.opt.listchars = { tab = "» ", trail = "·", nbsp = "␣" }`**
    Defines how invisible characters are displayed:

    - `tab` is shown as `»` .

    - Trailing spaces are shown as `·`.

    - Non-breaking spaces are shown as `␣`.

17. **`vim.opt.inccommand = "split"`**
    Shows the effects of a command (like substitution) in a split preview window as you type.

18. **`vim.opt.scrolloff = 0`**
    Sets the number of lines to keep above and below the cursor when scrolling. A value of `0` means no extra lines are shown.

19. **`vim.opt.hlsearch = true`**
    Highlights all matches of the current search pattern.

20. **`vim.opt.guicursor = ""`**
    Disables custom cursor shapes in GUI mode, using the default cursor instead.

21. **`vim.opt.nu = true`**
    Enables line numbers (same as `vim.opt.number = true`).

22. **`vim.o.background = "dark"`**
    Sets the background theme to dark mode, which affects color schemes.

23. **`vim.opt.relativenumber = true`**
    Displays line numbers relative to the current cursor position.

24. **`vim.opt.fillchars = { eob = " " }`**
    Replaces the `~` characters at the end of the buffer with a space for a cleaner look.

25. **`vim.opt.cursorline = true`**
    Highlights the current line where the cursor is located.

26. **`vim.opt.cursorcolumn = true`**
    Highlights the current column where the cursor is located.


---

### **Indentation and Tabs**

1. **`vim.opt.tabstop = 4`**
    Sets the width of a tab character to 4 spaces.

28. **`vim.opt.softtabstop = 4`**
    Makes the editor treat 4 spaces as a single tab when editing.

29. **`vim.opt.shiftwidth = 4`**
    Sets the number of spaces to use for each step of (auto)indentation.

30. **`vim.opt.expandtab = true`**
    Converts tabs into spaces.

31. **`vim.opt.smartindent = true`**
    Enables smart indentation based on the file type.


---

### **Text Wrapping**

1. **`vim.opt.wrap = true`**
    Enables line wrapping for long lines.


---

### **File Management**

1. **`vim.opt.swapfile = false`**
    Disables the creation of swap files.

34. **`vim.opt.backup = false`**
    Disables the creation of backup files.

35. **`vim.opt.undodir = os.getenv("HOME") .. "/.local/nvim/undodir"`**
    Sets the directory where undo files are stored.

36. **`vim.opt.undofile = true`**
    Enables persistent undo, allowing you to undo changes even after closing and reopening the file.


---

### **Search and Highlighting**

1. **`vim.opt.incsearch = true`**
    Enables incremental search, showing matches as you type.

38. **`vim.opt.isfname:append("@-@")`**
    Adds `@-@` to the list of characters considered part of a filename for commands like `gf`.


---

### **Mouse and GUI**

1. **`vim.opt.mouse = ""`**
    Disables mouse support in all modes.

40. **`vim.opt.termguicolors = true`**
    Enables true color support in the terminal, allowing for more vibrant color schemes.
