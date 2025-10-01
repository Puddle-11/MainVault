```dataviewjs
const backlook = 14;


const cutoff = new Date();
cutoff.setDate(cutoff.getDate() - backlook);


const days = [];
for (let i = backlook; i > 0; i--) 
{
  const d = new Date();
  d.setDate(d.getDate() - i);
  days.push(d.toISOString().slice(0,10));
}

const p_pages = dv.pages().where(p => p.file.ctime >= cutoff && p.User == "Puddle" && !p.file.tags.includes("#done") && p.file.tags.includes("#IKATODO"));
const p_counts = days.map(day => p_pages.filter(p => p.file.ctime.toFormat("yyyy-MM-dd") === day).length);

const o_pages = dv.pages().where(p => p.file.ctime >= cutoff && p.User == "Owi"&& !p.file.tags.includes("#done") && p.file.tags.includes("#IKATODO"));
const o_counts = days.map(day => o_pages.filter(p => p.file.ctime.toFormat("yyyy-MM-dd") === day).length);

const d_pages = dv.pages().where(p => p.file.ctime >= cutoff && p.User == "Dee"&& !p.file.tags.includes("#done") && p.file.tags.includes("#IKATODO"));
const d_counts = days.map(day => d_pages.filter(p => p.file.ctime.toFormat("yyyy-MM-dd") === day).length);

const chartData = {
  type: 'line',
  data: {
    labels: days,
    datasets: [{
      label: "Puddles Tasks",
      data: p_counts,
      borderColor: "#4f756a",
      fill: false,
      tension: 0.2,
      pointRadius: 0
      
    },
    {
      label: "Owens Tasks",
      data: o_counts,
      borderColor: "#ffb7c5",
      fill: false,
      tension: 0.2,
      pointRadius: 0
    },
    {
      label: "Dees Tasks",
      data: d_counts,
      borderColor: "#d5c1b7",
      fill: false,
      tension: 0.2,
      pointRadius: 0
    }
    ]
  }
};

window.renderChart(chartData, this.container);
```
