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

# Cheat Sheet

Local server-related:

```
npm install            // to install node stuff needed to run local server
npm run dev            // run local server that is needed to respond to the local 'dev mode' requests
```

Main project commands:

```
gleam run              // main command
gleam run -- --local   // source with tooltips
gleam run -- --fmt <x> // re-formats the source at x chars per line
```

Git cheat sheet:

```
git stash              // get rid of uncommitted local changes, but keep them in a 'stash' somewhere
git stash pop          // get the stashed changes back!
git add .              // stage all current changes
git commit -m "..."    // commit staged changes
git push               // push latest local commit(s) to remote
git pull               // get latest commits from remote (if anything)
git pull --rebase      // when a conflict arises during push or pull, try this; in worst case...
                       // ..."resolve in merge editor" inside of VSCode; after resolving, push again
```

# Known bugs

1. The `--local` mode has some layout artifacts to do with showing the tooltips. Only freak out if a layout bug shows in "normal mode" (without the tooltips).

2. Italics prevent line breaks if they end right before a punctuation mark. To fix this issue, write `this is _a sample long italic phrase that ends with a period._` instead of `this is _a sample long italic phrase that ends with a period_.`. But a proper fix is on the way, it won't always be like this!

# Html -> WLY ingestion

Steps: 

1. goto `~/github.com/vistuleB/wly`
2. `git pull`
3. goto `~/github.com/vistuleB`
4. `git clone git@github.com:vistuleB/ii2.git`
5. `cd ii2`
6. replace contents of `./public/pages` with the TI-1 `.html` source files (it currently contains TI-2 source files)
7. `rm -rf wly_content/*` (get rid of old TI-2 .wly output)
8. `gleam run -- --parse-html public/pages` & then work through errors (it will crash as soon as it finds an unmatched tag e.g., you have to fix unmatched tags manually; it might be picky about the .html structure in some other ways I can't remember; if the same pattern is repeatedly causing a crash then one can augment the function named `bad_html_pre_processor` found in `github.com/vistuleB/wly/vxml/vxml.gleam` to pre-process that pattern away)

Discrepancies in file naming conventions between TI-1 and TI-2 may also cause crashes in the last step, as the html-to-wly converter becomes confused how to name an output file; in that case just rename the files according the same convention as TI-2. (Or else edit the code to teach it how to parse TI-1 filenames, but I'm assuming the latter will be easier.)
