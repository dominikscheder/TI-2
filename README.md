# Installation

## 1. [Gleam Install](https://gleam.run/getting-started/installing)

## 2. Clone repos

Git clone `github.com/vistuleB/wly` and `github.com/vistuleB/ti2` next to each other in the same folder.

_SSH_

```
git clone git@github.com:vistuleB/wly.git
```

```
git clone git@github.com:vistuleB/ti2.git
```

_HTTPS_

```
git clone https://github.com/vistuleB/wly.git
```

```
git clone https://github.com/vistuleB/ti2.git
```

## 3. 'wly' test

1. `cd wly/desugaring`
2. `gleam run -m desugarers`

Various output should come out like this:

![wly/desugaring gleam run -m desugarers terminal output](writerly-desugaring-m-terminal-output.png)

## 4. 'ti2' test

1. go to `ti2` repo
2. `rm public/*.html`
3. `gleam run`

Various messages from the desugaring engine (situated in `wly` repo) should print out and the `public/` folder should have its .html repopulated.

To check, open `public/index.html` inside a browser.

## 5. Source location

Author source is contained in `wly/` folder.

In VSCode, download the [Writerly](https://marketplace.visualstudio.com/items?itemName=TabbyNotes.writerly-vscode-extension) extension for syntax highlighting.

## 6. Go-to-source tooltips (`--local` mode)

Run `npm install`, `npm run dev`, `gleam run -- --local`.

Do not forget to an ordinary `gleam run` before publishing again—you don't want to publish the go-to-source tooltips!

## 6. Source Formatter

Run `gleam run -- --fmt` for default 55 to reformat at char per line formatting or `gleam run -- --fmt <X>` to format line length to X chars per line.

## 8. Help

Run `gleam run -- --help` in `ti2` repo.

# Usage

Main commands:

```
gleam run              // main command
gleam run -- --local   // for 'local dev' mode with tooltip links, needs 'npm run dev' to be run
gleam run -- --fmt <x> // re-formats the source at x chars per line
```

