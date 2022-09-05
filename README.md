# realpath-compat

An implementation of realpath(1) that should work everywhere.

## Installation

Put the file anywhere you like, for example next to scripts where you need the
functionality to work on any POSIX-y platform.

## Usage

```sh
#!/bin/sh
set -e

# assuming you saved the realpath-compat file next to this script
my_real_path="$(./realpath-compat "$0")"
echo "This script's real path is: ${my_real_path}, and that's true even if you call it via a symlink."
```

## License

<p xmlns:cc="http://creativecommons.org/ns#" xmlns:dct="http://purl.org/dc/terms/"><a property="dct:title" rel="cc:attributionURL" href="https://github.com/hugojosefson/realpath-compat">realpath-compat</a> by <a rel="cc:attributionURL dct:creator" property="cc:attributionName" href="https://www.hugojosefson.com/">Hugo Josefson</a> is marked with <a href="http://creativecommons.org/publicdomain/zero/1.0?ref=chooser-v1" target="_blank" rel="license noopener noreferrer" style="display:inline-block;">CC0 1.0<img style="height:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/cc.svg?ref=chooser-v1"><img style="height:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/zero.svg?ref=chooser-v1"></a></p>
