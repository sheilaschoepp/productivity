---
title: "{{title}}"
created: "{{date}}"
accessed: "{{date}}"
tags:
related:
---

# Papers


```dataview
TABLE title AS Title, summary AS Summary
WHERE regexmatch(".*Literature Notes(/.*)?$", file.folder)
WHERE contains(indices, link("{{title}}"))
SORT file.name ASC
```

# Topics

```dataview
TABLE snapshot AS Snapshot
WHERE regexmatch(".*Permanent Notes(/.*)?$", file.folder)
WHERE contains(indices, link("{{title}}"))
SORT file.name ASC
```

# Citations

```dataview
TABLE
WHERE regexmatch(".*Citation Notes(/.*)?$", file.folder)
WHERE contains(indices, link("{{title}}"))
SORT file.name ASC
```