# total-lines

[![License GPL 3][badge-license]][copying]
[![MELPA Status][melpa-status-img]][melpa-status]

Keep track of a buffer's total number of lines.

`total-lines-mode` provides a variable, `total-lines` which holds the
total number of lines in the current buffer at any given time. It's
equivalent to `%L` in Vim's status line.

This mode requires GNU Emacs 24.3.

## Installation

With [`use-package`][use-package] in your init file:

```el
(use-package total-lines
  :ensure t
  :config (global-total-lines-mode))
```

## Usage

You could display it in your modeline:

```el
(setq-default mode-line-format
 `(; some
   ; other
   ; stuff
   ; the below will look like e.g. "263/947,10  26%"
   ((12 "%l" "/" (:eval (format "%d,%d" total-lines (1+ (current-column)))))
    (-3 "%p"))))
```

## How it works

When enabled, the mode counts all current lines in the buffer and adds
hooks to `before-change-functions` and `after-change-functions` to count
any lines that are subsequently added or removed.

Performance is very good since it is proportional to the sizes of edits.

## Support

You can ask a question in the [issue tracker][], or email me at
hinrik.sig@gmail.com.

## Contribute

Pull requests are welcome.

## License

total-lines is free software: you can redistribute it and/or modify it
under the terms of the GNU General Public License as published by the
Free Software Foundation, either version 3 of the License, or (at your
option) any later version.

total-lines is distributed in the hope that it will be useful, but
WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General
Public License for more details.

See [`COPYING`][copying] for the complete license.

[badge-license]: https://img.shields.io/badge/license-GPL_3-green.svg
[COPYING]: https://github.com/hinrik/total-lines/blob/master/COPYING
[GNU Emacs]: https://www.gnu.org/software/emacs/
[MELPA]: http://melpa.milkbox.net/
[melpa-status-img]: http://melpa.org/packages/total-lines.svg
[melpa-status]: http://melpa.org/#/total-lines
[use-package]: https://github.com/jwiegley/use-package
[Issue tracker]: https://github.com/hinrik/total-lines/issues
