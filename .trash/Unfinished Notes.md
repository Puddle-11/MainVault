# Resources
### Alpha
```dataview
list
from #alpha where file.folder != "MainNet/5. Templates"
SORT file.name asc
```
# Projects

### In Progress
```dataview
list
from #project
where !contains(file.tags, "#DONE") and file.folder != "MainNet/5. Templates"
```





