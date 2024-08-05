# Obsidian templates

## Content

A couple of simple markdown templates to be use with
[obsidian.nvim](https://github.com/epwalsh/obsidian.nvim)

It can be setup using this in the neovim configuration.

```lua
daily_notes = {
  folder = "dailies",
  default_tags = { "type/daily-notes" },
  template = "daily.md",
},
templates = {
  folder = "~/git/blaurent/obsidian-templates",
  date_format = "%A %B %Y",
  time_format = "%H:%M",
  substitutions = {
    year = function()
      return os.date("%Y", os.time())
    end,
    month = function()
      return os.date("%B", os.time())
    end,
    author = function()
      return os.capture("rg -N '(name = )(.*)' -or '$2' ~/.gitconfig", false)
    end,
    fulldate = function()
      return os.date("%A %e %B %Y", os.time())
    end,
    week = function()
      return os.date("W%V")
    end,
  },
},
```
