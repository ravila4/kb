---
id: 4beyy1jr7rxh18x0e5sw6vl
title: Conda
desc: 'Using Anaconda package manager'
updated: 1647065488740
created: 1647057729668
---

## Environment Management

### Updating all environment packages:

```
conda update --all
```

### Cloning an environment:

```
conda create -n new-env --clone base
```

### Exporting an environment:

```
conda env export | grep -v "^prefix: " > environment.yml
```

### Re-creating an environment from a file:

```
conda env create -f environment.yml
```

### Removing an environment

```
conda env remove -n ENV_NAME
```

