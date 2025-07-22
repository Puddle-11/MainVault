
## Todo
```dataview
table Deadline
from #TODO where Deadline > date(today)

```

## Due Today
```dataview
table Deadline
from #TODO where Deadline = date(today)

```


## Overdue
```dataview
table Deadline
from #TODO where Deadline < date(today)

```









