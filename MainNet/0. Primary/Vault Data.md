
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


const dcounts = days.map(day => 
	pages.filter(p =>
			{ 
			 const deletedDate = p["Date Deleted"];
			 
			return deletedDate && deletedDate.toFormat("yyyy-MM-dd") === day 
			
			}
		).length
	);

const dcumulativeCounts = [];
let drunningTotal = 0;

for (let i = 0; i < dcounts.length; i++) {
    drunningTotal += dcounts[i];        // add today's count
    dcumulativeCounts.push(drunningTotal); // store total so far
}
for(let i = 0; i < cumulativeCounts.length; i++){
	cumulativeCounts[i] = cumulativeCounts[i] - dcumulativeCounts[i];
}
const chartData = {
  type: 'line',
  data: {
    labels: days,
    datasets: [{
      label: "New notes / day",
      data: cumulativeCounts,
      borderColor: "#eb6134",
      backgroundColor: "#eb613430",
      fill: true,
      tension: 0.2,
      pointRadius: 0,
      borderWidth: 2
      
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
      backgroundColor: "#eb613430",
      borderColor: "#eb6134",
      borderWidth: 2
    }]
  }
};

window.renderChart(chartData, this.container);

```



