# chown-chmod-me: set file access control to solely me.

Syntax:

    chown-chmod-me [paths]

Example that uses the current path:

    chown-chmod-me

Example that uses the current path explicitly:

    chown-chmod-me .

Example that uses multiple paths:

    chown-chmod-me /foo /goo /hoo


 ## Implementation

This tool uses existing Unix commands:

  * Use the command `chown` to set the user and group.

  * Use the command `chmod` to remove non-user permissions.

  * Use the command `id` to get the user name and primary group name.

This tool is this simple:

```sh
chown -R "$(id -un):$(id -gn)" "$@"
chmod -R go= "$@"
```

We use this tool because it is easy and safe for people with a range of skill levels.

## Tracking

  * Command: chown-chmod-me
  * Version: 1.0.0
  * Created: 2020-06-27T19:37:04Z
  * Updated: 2020-06-27T20:55:27Z
  * License: GPL-2.0-only
  * Contact: [Joel Parker Henderson](http://joelparkerhenderson.com)
