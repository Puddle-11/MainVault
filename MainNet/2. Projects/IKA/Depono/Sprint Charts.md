---
tags:
  - prototype
  - alpha
Links: "[[Depono]]"
---

# Burn Down

```dataviewjs
const backlook = 44;


const cutoff = new Date();
cutoff.setDate(cutoff.getDate() - backlook);


const days = [];
for (let i = backlook; i >= 0; i--) 
{
  const d = new Date();
  d.setDate(d.getDate() - i);
  days.push(d.toISOString().slice(0,10));
}

const p_pages = dv.pages().where
(
	p => p.file.ctime >= cutoff 
	&& p.User == "Puddle" 
	&& p.file.tags.includes("#ikatodo")
	
);


const p_counts = days.map(day => 
{
	const addedCount = p_pages.filter
	(
		p => p["Date Assigned"] 
		&& p["Date Assigned"].toFormat("yyyy-MM-dd") <= day
	).length;
	
	const deletedCount = p_pages.filter
	(
		p => p["Date Deleted"] && p["Date Assigned"] 
		&& p["Date Deleted"].toFormat("yyyy-MM-dd") <= day
	).length
	
	return addedCount - deletedCount;
});


const o_pages = dv.pages().where
(
	p => p.file.ctime >= cutoff && p.User == "Owi" 
	&& p.file.tags.includes("#ikatodo")
);
const o_counts = days.map(day => {
	const addedCount = o_pages.filter
	(
		p => p["Date Assigned"] 
		&& p["Date Assigned"].toFormat("yyyy-MM-dd") <= day
	).length;
	
	const deletedCount = o_pages.filter
	(
		p => p["Date Deleted"] && p["Date Assigned"] 
		&& p["Date Deleted"].toFormat("yyyy-MM-dd") <= day
	).length
	
	return addedCount - deletedCount;
	
});

const d_pages = dv.pages().where
(
	p => p.file.ctime >= cutoff && p.User == "Dee" 
	&& p.file.tags.includes("#ikatodo")
);

const d_counts = days.map(day => {
	const addedCount = d_pages.filter
	(
		p => p["Date Assigned"] 
		&& p["Date Assigned"].toFormat("yyyy-MM-dd") <= day
	).length;
	
	const deletedCount = d_pages.filter
	(
		p => p["Date Deleted"] && p["Date Assigned"] 
		&& p["Date Deleted"].toFormat("yyyy-MM-dd") <= day
	).length
	
	return addedCount - deletedCount;
	
});

const chartData = 
{
  type: 'line',
  data: {
    labels: days,
    datasets: [{
      label: "Puddles Tasks",
      data: p_counts,
      borderColor: "#4f756a",
      fill: false,
      tension: 0,
      pointRadius: 0
      
    },
    {
      label: "Owens Tasks",
      data: o_counts,
      borderColor: "#ffb7c5",
      fill: false,
      tension: 0,
      pointRadius: 0
    },
    {
      label: "Dees Tasks",
      data: d_counts,
      borderColor: "#d5c1b7",
      fill: false,
      tension: 0,
      pointRadius: 0
    }
    ]
  }
};

window.renderChart(chartData, this.container);
```

# Burn Up
```dataviewjs
const backlook = 44;


const cutoff = new Date();
cutoff.setDate(cutoff.getDate() - backlook);


const days = [];
for (let i = backlook; i >= 0; i--) 
{
  const d = new Date();
  d.setDate(d.getDate() - i);
  days.push(d.toISOString().slice(0,10));
}

const pages = dv.pages().where
(
	p => p.file.ctime >= cutoff 
	&& p.file.tags.includes("#ikatodo")
	
);
const counts = days.map(day => 
{
	const deletedCount = pages.filter
	(
		p => p["Date Deleted"] && p["Date Assigned"] 
		&& p["Date Deleted"].toFormat("yyyy-MM-dd") <= day
	).length
	
	return deletedCount;
});

const scopeCount = days.map(day => 
{
	const addedCount = pages.filter
	(
		p => p["Date Assigned"] 
		&& p["Date Assigned"].toFormat("yyyy-MM-dd") <= day
	).length;
    return addedCount;
})

const layout = {
  yaxis: {
    range: [0, 100] // lock y-axis between 0 and 100
  }
};
const chartData = 
{
  type: 'line',
  data: {
    labels: days,
    datasets: [{
      label: "Tasks Completed",
      data: counts,
      borderColor: "#eb6134ff",
	  backgroundColor: "#eb613430",
      fill: true,
      tension: 0,
      pointRadius: 0
    },
    {
      label: "Scope",
      data: scopeCount,
      borderColor: "#FFFFFF",
      fill: false,
      tension: 0,
      pointRadius: 0
    }
    ]
  }
};

window.renderChart(chartData, this.container, layout);
```


---


### Puddle's Tasks
```dataview
list
from [[Feature List]] where User = "Puddle" and file.folder != "MainNet/7. Deleted"
```
### Owi's Tasks
```dataview
list
from [[Feature List]] where User = "Owi" and file.folder != "MainNet/7. Deleted"
```
### Dee's Tasks
```dataview
list
from [[Feature List]] where User = "Dee" and file.folder != "MainNet/7. Deleted"
```
