# keepass-dmenu

## Installation

```
git clone https://github.com/SapuSeven/keepass-dmenu.git
cd keepass-dmenu
python -m pip install .
```

## Configuration

The script is looking for a configuration file under `$XDG_CONFIG_HOME/keepass-dmenu.config`, falling back to `$HOME/.config/keepass-dmenu.config` if `XDG_CONFIG_HOME` is not set.

The file follows the INI file format.

### Example

 [`keepass-dmenu.config.example`](https://github.com/SapuSeven/keepass-dmenu/blob/master/keepass-dmenu.config.example) contains a template for the configuration file.

```
[config]
database=PATH_TO_DATABASE
password=PLAINTEXT_PASSWORD
keyfile=PATH_TO_KEYFILE
```

_Note: If you don't want to store the plaintext password, you currently need to rely on a keyfile stored at a secure location._

## Usage

_Note: You need to add the [Python site-package script directory](https://www.python.org/dev/peps/pep-0370/#specification) (default: `~/.local/bin`) to your PATH variable._

`list`: Simply returns all entries line-by-line with their full path.

`info`: Used to get details for a single entry. Requires additional arguments in the following format: `info <path> [user|pass|otp|custom] [customFieldName]`

### Example

`$ keepass-dmenu.py list`
```
Group 1/Entry 1
Group 1/Entry 2
Group 1/Entry 3
Group 2/Entry 1
```
---
`$ keepass-dmenu.py info "Group 1/Entry 1"`
```
Entry: "Group 1/Entry 1 (username)"
```
---
`$ keepass-dmenu.py info "Group 1/Entry 1" user`
```
username
```
---
`$ keepass-dmenu.py info "Group 1/Entry 1" otp`
```
123456
```
---
`$ keepass-dmenu.py info "Group 1/Entry 1" custom field1`
```
value1
```