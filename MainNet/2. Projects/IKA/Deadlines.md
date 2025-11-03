
# IKA To-dos

## General
```dataview


table Deadline
from #IKATODO where (Deadline > date(today) or Deadline = date(0001-01-01)) and file.folder != "MainNet/5. Templates"


```


## Due Today
```dataview
table Deadline
from #TODO where Deadline = date(today) and file.folder != "MainNet/5. Templates"

```


## Overdue
```dataview
table Deadline
from #IKATODO where Deadline < date(today) and file.folder != "MainNet/5. Templates" and Deadline != date(0001-01-01) and !contains(file.tags, "#DONE")

```
## Done
```dataview
list
from #IKATODO where contains(file.tags, "#DONE")
```






