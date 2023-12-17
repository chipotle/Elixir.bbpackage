# Elixir Package for BBEdit

Provides BBEdit Language support for [Elixir](http://elixir-lang.org). This package requires BBEdit 11 or higher; it has only been tested with BBEdit 14.

## Features

- Syntax highlighting with keywords current through Elixir 1.15
- Clippings for some common Elixir structures
- Bundled elixir-ls Language Server for smart completion and formatting (BBEdit 14+ only)

## Installation

### The easy way

Download the release version of the package with elixir-ls included, and double-click **Elixir.bbpackage**.

### The less easy way

1. Clone the repository to `Elixir.bbpackage`:

    git clone https://github.com/chipotle/bbedit-elixir.git Elixir.bbpackage

2. Download a current compiled release of `elixir-ls` from the release page:

    https://github.com/elixir-lsp/elixir-ls/releases

3. Unzip that release into a `Language Servers` subdirectory of the `Contents` subdirectory of the BBEdit package.

4. Now double-click **Elixir.bbpackage**.

## Configuration

In the Languages panel of BBEdit's Preferences, you can check the Elixir package's defaults and make any changes.

Defaults (should be configured "out of the box"):

- Line comment should be `#`, with no block comments
- Dash docsets should be configured for `elixir` and `erl` (Erlang)
- The language server should be enabled (BBEdit 14+ only), with the command `language_server.sh`, no arguments, language ID `elixir`.

The package can use different versions of elixir-ls if they are installed by setting the "Server Command" command path in BBEdit's Language Preference pane. The path should point to the `language_server.sh` file of the desired installation.

Recommendations:

- Turn on "Auto-expand tabs" and set tab width to 2
- Map the `eex` extension to HTML

BBEdit's codeless language modules don't support extending/embedding existing languages, so Elixir code inside EEX templates isn't highlighted.

## Language server features

- Function autocomplete
- Go to definition
- Show parameter help
- Reformat document (but not selection: all or nothing!)

## Caveats

The provided clippings and server-offered completions occasionally overlap (e.g., `def`, `function`). BBEdit shows clippings first, and you should generally prefer them.

While "Find Symbol in Workspace" is enabled, it generally jumps to Erlang code deep in Elixir's internal libraries rather than anywhere in the workspace. I suspect this is a misfeature on the elixir-ls side, not the BBEdit side.

## Version history

| Version | Release date | Notes                                            |  
| ------- | ------------ | ------------------------------------------------ |  
| 1.2.3   | 2023-12-17   | Regex bug fix for 1.2.2 (Erik Rose)              |  
| 1.2.2   | 2023-12-15   | Elixir 1.15, elixir-ls 0.17.10, bug fixes        |  
| 1.2.1   | 2022-12-31   | Elixir 1.14, elixir-ls 0.12.0                    |  
| 1.2.0   | 2022-10-10   | Elixir 1.14, elixir-ls 0.11.0                    |  
| 1.1.0   | 2022-01-14   | Elixir 1.13, elixir-ls 0.9.0                     |  
| 1.0.2   | 2021-07-25   | add keywords, tweak comment regex                |  
| 1.0.1   | 2021-07-21   | initial release for Elixir 1.12, elixir-ls 0.7.0 |  

## Credits

The language server is from the elixir-lsp project. This package was inspired by an earlier package, elixir_bbedit, by David H. Clements.

- <https://github.com/elixir-lsp/elixir-ls>
- <https://github.com/dclements/elixir_bbedit>
