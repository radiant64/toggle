# Toggle

A small POSIX (mostly) tool that toggles the availability of one or more files
in the filesystem. It operates by temporarily moving the disabled files to a
storage area, from where they can be moved back to their original location by
repeating the command.

## Installing

Copy or symlink the main 'toggle' script to somewhere in `PATH`. Optionally
copy or create configuration files.

## Usage

Toggle will temporarily hide any file or set of files specified, and reveal them
again by reissuing the command on the same path or set of paths. In addition, it
is possible to specify grouped sets of automatic rules for path generation.

Rules are specified in config files, residing in the `$XDG_CONFIG_HOME/toggle/`
directory. See the example files for usage.

`toggle -h` will provide more detailed information about flags and parameters.

## Example

This session transcript uses the bundled `githooks` sample configuration.

```
~/dev/project/src$ toggle githooks
Disabled /home/dave/dev/project/.git/hooks/prepare-commit-msg
Disabled /home/dave/dev/project/.git/hooks/update

~/dev/project/src$ toggle -l
Currently disabled files:

/home/dave/dev/project/.git/hooks/prepare-commit-msg   (prepare-commit-msg)
/home/dave/dev/project/.git/hooks/update   (update)

~/dev/project/src$ toggle githooks update
Enabled /home/dave/dev/project/.git/hooks/update
```

## License

MIT

