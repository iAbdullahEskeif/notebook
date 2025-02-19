---
created: 2025-02-19
tags:
  - neovim
  - linux
  - configs
---
- So here in the `lua module` `vim.keymap` we have 2 methods the first one is `del`

```lua
vim.keymap.del({modes}, {lhs}, {opts})                    
```

- Remove an existing mapping. Examples: 

```lua
-- Example 1:
        vim.keymap.del('n', 'lhs')
-- Example 2:
        vim.keymap.del({'n', 'i', 'v'}, '<leader>w', { buffer = 5 })
```

- Parameters:
    • {modes}  (`string|string[]`)
    • {lhs}    (`string`)
    • {opts}   (`table?`) A table with the following fields:
         • {buffer}? (`integer|boolean`) Remove a mapping from the
            given buffer. When `0` or `true`, use the current buffer.

- The second method is set and it is pretty clear what it does.

```lua
vim.keymap.set({mode}, {lhs}, {rhs}, {opts}) 
```

  Adds a new |mapping|. Examples:
  
```lua
-- Map to a Lua function:
vim.keymap.set('n', 'lhs', function() print("real lua function") end)
-- Map to multiple modes:
vim.keymap.set({'n', 'v'}, '<leader>lr', vim.lsp.buf.references, { buffer = true })
--Buffer-local mapping:
vim.keymap.set('n', '<leader>w', "<cmd>w<cr>", { silent = true, buffer = 5 })
-- Expr mapping:
 vim.keymap.set('i', '<Tab>', function()
return vim.fn.pumvisible() == 1 and "<C-n>" or "<Tab>"
end, { expr = true })
-- <Plug> mapping:
vim.keymap.set('n', '[%%', '<Plug>(MatchitNormalMultiBackward)')
```

- Parameters:
	• {mode}  (`string|string[]`) Mode short-name, see |nvim_set_keymap()|.
	  Can also be list of modes to create mapping on multiple modes.
	• {lhs}   (`string`) Left-hand side |{lhs}| of the mapping.
	• {rhs}   (`string|function`) Right-hand side |{rhs}| of the mapping can    be a Lua function.
	• {opts}  (`table?`) Table of |:map-arguments|. 
		Same as |nvim_set_keymap()| {opts}, except:
			 • {replace_keycodes} defaults to `true` if "expr" is `true`.
		Also accepts:
		    • {buffer}? (`integer|boolean`) Creates buffer-local mapping, `0` or `true` for        current buffer.
		  • {remap}? (`boolean`, default: `false`) Make the mapping
			     recursive. Inverse of {noremap}.




