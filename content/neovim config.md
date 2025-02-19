---
created: 2025-02-19 00:44
tags: []
---

# the file structure:

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