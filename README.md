# skink-mode

A basic Emacs major mode for the [Skink](https://github.com/markoxley/skink) programming language.

This is a minimal plugin that provides:

- Syntax highlighting (keywords, builtin types, constants, declarations)
- `//` line comment support
- Brace-based indentation
- `{expr}` string-interpolation highlighting
- Attribute highlighting, e.g. `[db(pk,auto)]`
- Automatic activation for `*.skink` files

## Requirements

- Emacs 25.1 or later (uses `define-derived-mode` with `prog-mode`)

## Installation

`skink-mode` is not on MELPA, but it can be installed directly from
[GitHub](https://github.com/markoxley/skink-emacs) — or copied manually.

### package-vc-install (Emacs 29+)

```elisp
(package-vc-install "https://github.com/markoxley/skink-emacs")
```

### use-package `:vc` (Emacs 30+)

```elisp
(use-package skink-mode
  :vc (:url "https://github.com/markoxley/skink-emacs"
            :rev :newest)
  :mode "\\.skink\\'")
```

### straight.el

```elisp
(use-package skink-mode
  :straight (:host github :repo "markoxley/skink-emacs")
  :mode "\\.skink\\'")
```

### Doom Emacs

In `packages.el`:

```elisp
(package! skink-mode :recipe (:host github :repo "markoxley/skink-emacs"))
```

In `config.el`:

```elisp
(use-package! skink-mode
  :mode "\\.skink\\'")
```

### Manual installation

1. Clone or download this repo and copy `skink-mode.el` somewhere on your
   `load-path`, e.g.:

   ```sh
   git clone https://github.com/markoxley/skink-emacs ~/.emacs.d/skink-emacs
   ```

2. Add the following to your init file (`~/.emacs`, `~/.emacs.d/init.el`, or `~/.config/emacs/init.el`):

   ```elisp
   (add-to-list 'load-path "~/.emacs.d/skink-emacs")
   (require 'skink-mode)
   ```

## Usage

Once installed, `skink-mode` activates automatically for files ending in `.skink`. You can also enable it manually with `M-x skink-mode`.

### Customization

Indentation width defaults to 4 spaces. To change it:

```elisp
(setq skink-indent-offset 2)
```

or via `M-x customize-group RET skink RET`.

## Limitations

This is intentionally a basic mode — it does not provide LSP integration, completion, formatting, or navigation. Indentation is a simple heuristic based on the previous nonblank line.

## Language Server (LSP)

`skink-mode` registers `skink-lsp` with both **eglot** (built-in since
Emacs 29) and **lsp-mode** automatically when either is loaded — no
extra config beyond having `skink-lsp` on `PATH` (or set
`skink-lsp-program` for a custom binary path).

- eglot: `M-x eglot` in a `.skink` buffer (or `M-x skink-eglot-ensure`)
- lsp-mode: `M-x lsp` in a `.skink` buffer

Server features: completion, hover, diagnostics, go-to-definition,
references, rename, formatting, semantic tokens.
