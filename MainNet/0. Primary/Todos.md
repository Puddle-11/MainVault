
## Todo
```dataview


table Deadline, User
from #TODO where (Deadline > date(today) or Deadline = date(0001-01-01)) and file.folder != "MainNet/5. Templates"


```
## Due Today
```dataview
table Deadline, User
from #TODO where Deadline = date(today) and file.folder != "MainNet/5. Templates"

```
## Overdue
```dataview
table Deadline, User
from #TODO where Deadline < date(today) and file.folder != "MainNet/5. Templates" and Deadline != date(0001-01-01)

```
## Done
```dataview
table Deadline, User
from #DONE where file.folder != "MainNet/5. Templates"
```









