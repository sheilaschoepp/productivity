---
title: "{{title}}"
created: "{{date}}"
accessed: "{{date}}"
tags: 
related:
---

# Papers

```dataview
TABLE title AS Title
FROM "Literature Notes"
WHERE index = [[{{title}}]]
```

# Topics

```dataview
TABLE
FROM "Permanent Notes"
WHERE index = [[{{title}}]]
```
