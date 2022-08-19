---
id: pzlgua942o4wzmg1tjntnyc
title: Scripts
desc: ''
updated: 1660082822144
created: 1647059949753
---

This document collects basic syntax and best practices for writing
BASH scripts.

## Starting scripts

It is good practice to start BASH scripts with the following lines:

```bash
#!/bin/bash

set -euo pipefail
```
### Set

The command `set` allows you to change shell options. The most useful flags are:

-e
: Stop execution when an error is encountered.
You can "catch" an error to prevent the shell from exiting by appending `|| true` after a failing command.

-o pipefail
: Catch errors in pipes. Return zero exit status only if all commands in a pipeline succeed.

-u
: Error out when shell encounters undefined variables by their values.

-x
: Debug mode. Prints every line and output, substituting variables

-f
: Disable file globbing.

