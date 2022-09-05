# realpath-compat

An implementation of [realpath(1)](https://linux.die.net/man/1/realpath) that
should work everywhere.

## Installation

Copy this function into your shell script:

```sh
realpath_compat(){ if [ $# -eq 0 ];then echo "Usage: realpath_compat FILE [FILE ...]">&2;return 1;fi;while [ $# -gt 0 ];do file="$1";shift;if ! [ -e "$file" ];then echo "realpath_compat: $file: No such file or directory">&2;return 1;fi;realpath "$file" 2>/dev/null||readlink -f "$file" 2>/dev/null||zsh -c 'echo ${0:A}' "$file" 2>/dev/null||python3 -c "import os; import sys; print(os.path.realpath(sys.argv[1]))" "$file" 2>/dev/null||node -e "console.log(require('fs').realpathSync(process.argv[1]))" "$file" 2>/dev/null||echo "realpath_compat: $file: Could not resolve real path">&2;done;}
```

Alternatively, copy the non-minified version found in
[realpath-compat](realpath-compat#L6-L30).

## Usage

Call the function, with some file(s) as argument(s).

Example:

```sh
#!/bin/sh
set -e

realpath_compat(){ if [ $# -eq 0 ];then echo "Usage: realpath_compat FILE [FILE ...]">&2;return 1;fi;while [ $# -gt 0 ];do file="$1";shift;if ! [ -e "$file" ];then echo "realpath_compat: $file: No such file or directory">&2;return 1;fi;realpath "$file" 2>/dev/null||readlink -f "$file" 2>/dev/null||zsh -c 'echo ${0:A}' "$file" 2>/dev/null||python3 -c "import os; import sys; print(os.path.realpath(sys.argv[1]))" "$file" 2>/dev/null||node -e "console.log(require('fs').realpathSync(process.argv[1]))" "$file" 2>/dev/null||echo "realpath_compat: $file: Could not resolve real path">&2;done;}

my_real_path="$(realpath_compat "$0")"
echo "This script's real path is: ${my_real_path}, and that's true even if you call it via a symlink."
```

## License

<p xmlns:cc="http://creativecommons.org/ns#" xmlns:dct="http://purl.org/dc/terms/"><a property="dct:title" rel="cc:attributionURL" href="https://github.com/hugojosefson/realpath-compat">realpath-compat</a> by <a rel="cc:attributionURL dct:creator" property="cc:attributionName" href="https://www.hugojosefson.com/">Hugo Josefson</a> is marked with <a href="http://creativecommons.org/publicdomain/zero/1.0?ref=chooser-v1" target="_blank" rel="license noopener noreferrer" style="display:inline-block;">CC0 1.0<img style="height:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/cc.svg?ref=chooser-v1"><img style="height:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/zero.svg?ref=chooser-v1"></a></p>
