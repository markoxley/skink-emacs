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

`skink-mode` is not on MELPA or any other package archive, so install it manually.

### Manual installation

1. Copy `skink-mode.el` somewhere on your `load-path`, e.g.:

   ```sh
   mkdir -p ~/.emacs.d/lisp
   cp skink-mode.el ~/.emacs.d/lisp/
   ```

2. Add the following to your init file (`~/.emacs`, `~/.emacs.d/init.el`, or `~/.config/emacs/init.el`):

   ```elisp
   (add-to-list 'load-path "~/.emacs.d/lisp")
   (require 'skink-mode)
   ```

### use-package

If you use `use-package`, point it at the file directly:

```elisp
(use-package skink-mode
  :load-path "~/path/to/skink-emacs"
  :mode "\\.skink\\'")
```

Or with `straight.el`:

```elisp
(use-package skink-mode
  :straight (:local-repo "~/path/to/skink-emacs")
  :mode "\\.skink\\'")
```

### Doom Emacs

In `packages.el`:

```elisp
(package! skink-mode :recipe (:local-repo "~/path/to/skink-emacs"))
```

In `config.el`:

```elisp
(use-package! skink-mode
  :mode "\\.skink\\'")
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
