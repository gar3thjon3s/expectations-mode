# Expectations Mode

[![Circle CI](https://circleci.com/gh/clojure-expectations/expectations-mode.svg?style=svg)](https://circleci.com/gh/clojure-expectations/expectations-mode)

A minor Emacs mode for running
[Expectations](https://github.com/jaycfields/expectations), based upon
[Clojure test
mode](https://github.com/technomancy/clojure-mode/blob/master/clojure-test-mode.el).

Note that this is designed for classic expectations, and will not work with the
[clojure.test version](https://github.com/clojure-expectations/clojure-test)

## Important

This package has some major breakage due to changes in the cider API and removal of
legacy Emacs functions.

It is probably better to look at CIDER's built-in test features. [CIDER has
several functions to help you run all your
tests](https://docs.cider.mx/cider/testing/running_tests.html).

## Installation

*Please note Expectations v1.3.7 or greater is required to use expectations-mode.*

expectations-mode is not in MELPA, so you must install the package manually.

Download expectations-mode.el, put it somewhere on your Emacs load path, and
require it inside of init.el

```lisp
(require 'expectations-mode)
```

This will add a `clojure-mode-hook` to enable `expectations-mode`
whenever a Clojure test file is opened that has a namespace with
'expectations.' or '-expectations' inside of it.

For example namespaces like...

```lisp
(ns myproject.expectations.core
  (:use expectations))

(ns myproject.core-expectations
  (:use expectations))
```

...will cause `expectations-mode` to automatically activate. Where as
namespaces like:

```lisp
(ns myproject.test.core
  (:use clojure.test))
```

...will be ignored.

## Colours

Expectations colourises its output by default. To turn this off and
get rid of the annoying characters in your output, add this to your
init.el in an appropriate place:

```lisp
(setenv "EXPECTATIONS_COLORIZE" "false")
```

## Usage

Current key mappings are:

```
C-c ,    run tests in ns
C-c C-,  run tests in ns
C-c k    clear test results
C-c '    show message for test under cursor
```

The keybindings are a subset of the bindings used in
`clojure-test-mode` and work the same way.

The shortcuts to run individual tests are not required, as you
generally use the `-focus` version of the expectations macros to run
an expectation in isolation.

## License

Distributed under the GNU General Public License; see C-h t to view.
