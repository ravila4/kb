---
id: lkcpotdu9x59v4mh3u6z077
title: VS Code
desc: 'How to do some useful things with VS Code'
updated: 1658960156340
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