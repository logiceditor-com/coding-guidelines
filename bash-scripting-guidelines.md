Bash scripting guidelines
=========================

## Interpreter

For better portability be sure to specify the interpreter in this way:
```shell
#! /usr/bin/env bash
```

## Set options

For prevent hidden bugs use `set -euox pipefail` as the first command 
when possible.
For additional info, please see
[manpages](http://manpages.ubuntu.com/manpages/hirsute/en/man1/set.1posix.html)

## Variables

Variables local to the script must be in the lower case.

Using variable is allowed only wrapped in `"${}"`.
Example:
```shell
var=123
echo "${var}"
```

If you need to use `"$@"`, always use quotation marks.
Example:
```shell
lua test/test.lua "$@"
```

If the script is sensitive to the current directory, store it in the `ROOT`
variable. Example:
```shell
ROOT="${BASH_SOURCE[0]}"
if([ -h "${ROOT}" ]) then
  while([ -h "${ROOT}" ]) do ROOT=`readlink "${ROOT}"`; done
fi
ROOT=$(cd `dirname "${ROOT}"` && pwd)
```

## Wrapping other programs

If the script is a wrapper around another program and no postprocessing is 
needed after execution of that program, you should strive to replace the shell 
without creating additional processes, using `exec`. Execution of the wrapper 
script will be terminated after the `exec` call.
Example:
```shell
exec /usr/bin/env "${LE_LUA_INTERPRETER}" "$@"
```
