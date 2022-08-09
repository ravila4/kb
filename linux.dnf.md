---
id: jfrgnj07atr3cmvedlxjmmw
title: dnf
desc: 'Using the dnf package manager'
updated: 1660082445991
created: 1660081957849
---

## List installed repositories

```bash
yum repolist
yum repolist disabled  # disabled repos
```

## Disable a repository


```bash
dnf config-manager --set-disabled repository
```
