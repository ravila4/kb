---
id: lkcpotdu9x59v4mh3u6z077
title: VS Code
desc: 'How to do some useful things with VS Code'
updated: 1660080688973
created: 1658941676755
---

How to do some useful things with VS Code.


## Useful keyboard shortcuts

### Vim extension shortcuts:

| Shortcut | Description                                     |
| -------- | ----------------------------------------------- |
| `gh`     | Show type of the symbol under the cursor        |
| `gd`     | Go to definition of the symbol under the cursor |

### VSCode shortcuts:

| Shortcut           | Description                       |
| ------------------ | --------------------------------- |
| `Ctrl + Shift + N` | New empty window                  |
| `Alt + Shift + P`  | Open recent projects              |
| `Alt + ↓↑`         | Move the current line up or down. |
| `F2`               | Rename the current symbol         |

## Testing

### Configuring testing

Add to workspace settings.json:

```json
{
    "python.testing.autoTestDiscoverOnSaveEnabled": true,
    "python.testing.pytestEnabled": true,
    "python.testing.pytestPath": "pytest"
}
```

## Technical Issues

### Fedora installation

### Escaping the Flatpak sandbox

Flatpak installations start a sandboxed shell that doesn't have access to the host's system packages.

To fix this, I originally used `flatpak-spawn` to start a shell. The settings under `terminal.integrated.profiles.linux` are:

```json
    "Host: Bash (new pty)": {
        "path": "/usr/bin/flatpak-spawn",
        "args": [
            "--env=TERM=vscode",
            "--host",
            "script",
            "--quiet",
            "/dev/null"
        ]
    },
    "Host: ZSH (new pty)": {
        "path": "/usr/bin/flatpak-spawn",
        "args": [
            "--env=TERM=vscode",
            "--env=SHELL=zsh",
            "--host",
            "script",
            "--quiet",
            "/dev/null"
        ]
    }
```

A better solution was to use 'host-spawn`: https://github.com/1player/host-spawn to start a shell:

```json

"terminal.integrated.profiles.linux": {
    "Host: Bash (host-spawn)": {
        "path": "/home/ravila/.local/bin/host-spawn",
        "args": [
            "bash"
        ]
    }
}
```