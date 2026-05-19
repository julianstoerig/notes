---
title: file archives
tags: [it, linux]
date: 2026-05-18
id: cqts
author: Julian Stoerig
---

There are different programs for creating various archive types.

## `.tar.gz` archives

These should be preferred on linux as they tend to create smaller archives, but are unknown to most windows users.

```bash
# create archive:
# The -f flag takes the archive name as argument, so it must come *immediately* before that!
tar -czf <archive-name>.tar.gz <dir-to-archive-name>
# unpack archive
tar -xzf <archive-name>.tar.gz
```
