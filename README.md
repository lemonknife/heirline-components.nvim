# [heirline-components.nvim](https://github.com/Zeioth/heirline-components.nvim)
Distro agnostic components for your Neovim heirline config.

![screenshot_2024-02-14_00-54-13_735661835](https://github.com/Zeioth/heirline-components.nvim/assets/3357792/f6d732f9-48b4-46e7-a15d-9fc03c68d434)

This is how the components above look on the statusline.
![screenshot_2024-02-14_20-37-46_332356599](https://github.com/Zeioth/heirline-components.nvim/assets/3357792/22c8de7d-20ce-456a-834d-1dd77064b2ee)

<div align="center">
  <a href="https://discord.gg/ymcMaSnq7d" rel="nofollow">
      <img src="https://img.shields.io/discord/1121138836525813760?color=azure&labelColor=6DC2A4&logo=discord&logoColor=black&label=Join the discord server&style=for-the-badge" data-canonical-src="https://img.shields.io/discord/1121138836525813760">
    </a>
</div>

## Table of contents

- [Why](#why)
- [How to install](#how-to-install)
- [Components](#components)
- [Available options](#available-options)
- [Example config](#example-config)
- [FAQ](#faq)

## Why
[Heirline](https://github.com/rebelot/heirline.nvim) is a engine to create your own Neovim user interface. This comes at a price though: increased complexity. To avoid that problem, I've decided to compile this collection of components you can fork and modify. That way you have a safe and well tested starting point to hopefuly save you a lot of time.

## How to install
Add it as a dependency of heirline

```lua
{
  "rebelot/heirline.nvim",
  dependencies = { "Zeioth/heirline-components.nvim" },
  opts = {},
    config = function(_, opts)
      local heirline = require "heirline"
      local heirline_components = require "heirline-components.all"

      -- Setup
      heirline_components.init.subscribe_to_events()
      heirline.load_colors(heirline_components.hl.get_colors())
      heirline.setup(opts)
    end,
}
```

## Components
### Statusline components

| Component | Description |
|-----------|-------------|
| [fill](https://github.com/Zeioth/heirline-components.nvim/wiki/fill) | A Heirline component for filling in the empty space of the bar. |
| [file_info](https://github.com/Zeioth/heirline-components.nvim/wiki/file_info) | A function to build a set of children components for an entire file information section. |
| [file_encoding](https://github.com/Zeioth/heirline-components.nvim/wiki/file_encoding) | Displays operative system and file encoding. |
| [nav](https://github.com/Zeioth/heirline-components.nvim/wiki/nav) | A function to build a set of children components, like line number, or the current navigation %. |
| [cmd_info](https://github.com/Zeioth/heirline-components.nvim/wiki/cmd_info-component) | A function to build a set of children components for information shown in the cmdline, like a macro recording indicator, or the search results. |
| [mode](https://github.com/Zeioth/heirline-components.nvim/wiki/mode-component) | A function to build a set of children components for a mode section. By default it only show colors, but it can be configured to show NORMAL, INSERT... etc like in classic vim. |
| [git_branch](https://github.com/Zeioth/heirline-components.nvim/wiki/git-branch) | A function to build a set of children components for a git branch section. |
| [git_diff](https://github.com/Zeioth/heirline-components.nvim/wiki/git-diff) | A function to build a set of children components for a git difference section. |
| [diagnostics](https://github.com/Zeioth/heirline-components.nvim/wiki/diagnostics) | A function to build a set of children components for a diagnostics section. |
| [treesitter](https://github.com/Zeioth/heirline-components.nvim/wiki/treesitter) | A function to build a set of children components for a Treesitter section. |
| [lsp](https://github.com/Zeioth/heirline-components.nvim/wiki/lsp%E2%80%90component) | A function to build a set of children components for an LSP section. `Warning`: This component only works out of the box on NormalNvim because it requires you add some logic to `lsp` and `lspconfig`. Click the component name to learn how to do it, or add the plugin [noice.nvim](https://github.com/folke/noice.nvim) as drop-in replacement for this component. |
| [virtual_env](https://github.com/Zeioth/heirline-components.nvim/wiki/virtual_env) | A function to build a component that show the current python virtual env. |
| [compiler_state](https://github.com/Zeioth/heirline-components.nvim/wiki/compiler_state) | Display a spinner while [compiler.nvim](https://github.com/Zeioth/compiler.nvim) is running. This component is also compatible with [overseer](https://github.com/stevearc/overseer.nvim). |

### Winbar components

| Component | Description |
|-----------|-------------|
| [breadcrumbs_when_inactive](https://github.com/Zeioth/heirline-components.nvim/wiki/breadcrumbs_when_inactive) | A function to build an alternative breadcrumbs component when the window is inactive. |
| [breadcrumbs](https://github.com/Zeioth/heirline-components.nvim/wiki/breadcrumbs) | A function to build a set of children components for an LSP breadcrumbs section. |

### Tabline components

| Component | Description |
|-----------|-------------|
| tabline_conditional_padding | A function to add padding to the tabine under certain conditions. The amount of padding is defined by the provider, which by default is self-caltulated based on the opened panel. |
| tabline_buffers | A function to build a visual component to display the available listed buffers of the current tab. |
| tabline_tabpages | A function to build a visual component to display the available tabpages. |

### Statuscolumn components

| Component | Description |
|-----------|-------------|
| foldcolumn | A function to build a set of components for a foldcolumn section in a statuscolumn. |
| numbercolumn | A function to build a set of components for a numbercolumn section in statuscolumn. |
| signcolumn | A function to build a set of components for a signcolumn section in statuscolumn. |

## Available options
You can customize icons and colors in a easy way.

| Option |
|--------|
| [icons](https://github.com/Zeioth/heirline-components.nvim/wiki/icons) |
| [colors](https://github.com/Zeioth/heirline-components.nvim/wiki/colors) |

For example:
```lua
"rebelot/heirline.nvim",
dependencies = {
  {
    "Zeioth/heirline-components.nvim",
    opts = {
      icons = { DiagnosticError = ";D" }
      colors = nil
    }
  }
}
```

## Example config
You can find the example config we use for NormalNvim [here](https://github.com/NormalNvim/NormalNvim/blob/98be877c6bac59dff495f5c6aabe4e20832bdb90/lua/plugins/2-ui.lua#L282).

## Credits
Currently, most of the GPL3 lua components this plugin use come from AstroNvim and NormalNvim. So please support both projects if you enjoy this plugin.

## FAQ
* **How can I contribute with a component?** Clone this repo. Go to [core.component.lua](https://github.com/Zeioth/heirline-components.nvim/blob/main/lua/heirline-components/core/component.lua) and create yours there. Then open a PR.
* **How do components work?** A component is made of providers. So you can use providers to build your component. Aditionally, conditions are used to decide when a component should be displayed. These components have been tested on nvim `v0.9.x`
* **How can I avoid breaking changes?** Always use the components by importing `heirline-components.all`. That way internal changes won't affect you. If you wanna be extra sure, you can also lock the plugin version in your package manager to avoid getting updates.
* **Why I can't see the `git_branch` and `git_diff` components?** You must have the plugin gitsigns installed. This is because both components use the event 'GitSignsUpdate' to check when your repo changes.

## 🌟 Support the project
If you want to help me, please star this repository to increase the visibility of the project.

[![Stargazers over time](https://starchart.cc/Zeioth/heirline-components.nvim.svg)](https://starchart.cc/Zeioth/heirline-components.nvim)
