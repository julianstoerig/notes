---
title: find and replace across file on linux
tags: [it, unix]
date: 2026-05-19T15:30:53
id: t8zt
---

To find and replace files on linux, the obvious choice are the standard unix tools.

## Preview Matches

You can preview where your proposed query will match using `grep`:

```bash
grep -n <old-text> <file-glob>
```

where `-n` shows line numbers. Adding `-R` makes it recursive and adding `-i` makes it case-insensitive.

## Find and Replace

`find` can be used to select the files and call `sed` via its `-exec` flag to actually replace text.

It is important to use `-name <name>` to restrict the file extension: `-name "*.c"`. This avoids corrupting binary files.

There is a flag for `sed`, `-i.bak`, that creates backups of every file on which a change is performed.

Using these best practices, a simple command is:

```bash
find . -type f -name ".c" -exec sed -i 's|<old-text>|<new-text>|g' {} +
```
