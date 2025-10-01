---
tags:
  - resource
  - alpha
  - "#area"
Area: "[[Resources]]"
---

# Movies
```dataview
table
Genre
from [[]] where file.folder != "MainNet/5. Templates" and Classification = "Movie"
sort Genre desc
```

# Anime
```dataview
table
Genre
from [[]] where file.folder != "MainNet/5. Templates" and Classification = "Anime"
sort Genre desc
```

# Shows
```dataview
table
Genre
from [[]] where file.folder != "MainNet/5. Templates" and Classification = "Show"
sort Genre desc
```

## Resources
