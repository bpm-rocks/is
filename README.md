BPM Library: Is
===============

Test if a variable exists, if it is an array and if it is a function.

The library adds functions to a Bash environment so your shell scripts can leverage this extra functionality. Though it is intended to be included with [BPM](http://bpm.sh), that is not strictly necessary because this has no dependencies.


Installation
============

Add to your `bpm.ini` file the following dependency.

    [dependencies]
    0=is

Run `bpm install` to add the library. Finally, use it in your scripts.

    #!/usr/bin/env bash
    . bpm
    bpm::include is


API
===


[//]: # (AUTOGENERATED FROM libis - START)

`is::array()`
-------------

Determine if a given environment variable exists and if it is an array.

* $1 - Name of environment variable.

Examples

    var=(abc)

    if is::array var; then
        echo "This is an array"
        echo "Be careful to use the variable's name in the function call."
    fi

    right=wrong
    wrong=()

    if is::array $right; then
        echo "This also says it is an array, which is incorrect."
        echo 'The correct call is `is::array right` without the $.'
    fi

Returns true (0) if the named variable exists and if it is an array. Returns false (1) otherwise.


`is::function()`
----------------

Determine if the given name is a defined function.

* $1 - Function name to check.

Examples

    moo () {
        echo "This is a function"
    }

    if is::function moo; then
        echo "moo is a defined function"
    fi

Returns true (0) if the name is a function, false (1) otherwise.


`is::set()`
-----------

Determine if a variable is assigned, even if it is assigned an empty value.

* $1 - Variable name to check.

Examples

    unset abc

    if ! is::set abc; then
        echo "The variable is not set"
    fi

    abc=""

    if is::set abc; then
        echo "This is true, the variable is set"
    fi

Returns true (0) if the variable is set, false (1) if the variable is unset.

[//]: # (AUTOGENERATED FROM libis - END)


License
=======

This project is placed under an [MIT License](LICENSE.md).
