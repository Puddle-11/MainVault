
# Vault Growth
```dataviewjs
const backlook = 60;


const cutoff = new Date();
cutoff.setDate(cutoff.getDate() - backlook);


const pages = dv.pages().where(p => p.file.ctime >= cutoff);
const days = [];

for (let i = backlook; i >= 0; i--) 
{
  const d = new Date();
  d.setDate(d.getDate() - i);
  days.push(d.toISOString().slice(0,10));
}

const counts = days.map(day => pages.filter(p => p.file.ctime.toFormat("yyyy-MM-dd") === day).length);

const cumulativeCounts = [];
let runningTotal = 0;

for (let i = 0; i < counts.length; i++) {
    runningTotal += counts[i];        // add today's count
    cumulativeCounts.push(runningTotal); // store total so far
}


const chartData = {
  type: 'line',
  data: {
    labels: days,
    datasets: [{
      label: "New notes / day",
      data: cumulativeCounts,
      borderColor: "rgba(153,102,255,1)",
      fill: false,
      tension: 0,
      pointRadius: 0
      
    }]
  }
};

window.renderChart(chartData, this.container);
```

# Tags
```dataviewjs



const pages = dv.pages();
const tagCounts = {};

for (let p of pages) 
{
	for (let tag of (p.file.tags ?? [])) 
	{
		tagCounts[tag] = (tagCounts[tag] || 0) + 1;
	}
}

const labels = Object.keys(tagCounts);
const values = Object.values(tagCounts);

const chartData = {
  type: 'bar',
  data: {
    labels: labels,
    datasets: [{
      label: "Notes per tag",
      data: values,
      backgroundColor: "rgba(75,192,192,0.4)",
      borderColor: "rgba(75,192,192,1)",
      borderWidth: 1
    }]
  }
};

window.renderChart(chartData, this.container);

```



