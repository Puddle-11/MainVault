
## Todo
```dataview
table Deadline
from #TODO where Deadline > date(today) and file.folder != "MainNet/5. Templates"

```


## Due Today
```dataview
table Deadline
from #TODO where Deadline = date(today) and file.folder != "MainNet/5. Templates"

```



## Overdue
```dataview
table Deadline
from #TODO where Deadline < date(today) and file.folder != "MainNet/5. Templates"

```



## Done

```dataview
table Deadline
from #DONE where file.folder != "MainNet/5. Templates"

```









