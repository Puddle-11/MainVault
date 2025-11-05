---
tags:
  - "#resource"
  - "#alpha"
Area: "[[Mathematics]]"
Var1: 2
Resolution: 100
---

# Math Functions
```dataviewjs

const label = new Array(dv.current().Resolution);
for(let i = 0; i < label.length; i++)
{
    label[i] = i;
}
const linear = new Array(dv.current().Resolution);
for(let i = 0; i < linear.length; i++)
{
    linear[i] = i;
}
const Pow = new Array(dv.current().Resolution);
for(let i = 0; i < Pow.length; i++)
{
    Pow[i] = i ** dv.current().Var1;
}
const log = new Array(dv.current().Resolution);
for(let i = 0; i < log.length; i++)
{
    log[i] = Math.log10(i);
}
const chartData1 = 
{
  type: 'line',
  data: {
    labels: label,
    datasets: [{
      label: "Power",
      data: Pow,
      borderColor: "#eb6134ff",
      fill: false,
      tension: 0,
      pointRadius: 0
    }
    ]
  }
};
const chartData2 = 
{
  type: 'line',
  data: {
    labels: label,
    datasets: [{
      label: "Linear",
      data: linear,
      borderColor: "#eb6134ff",
      fill: false,
      tension: 0,
      pointRadius: 0
    }
    ]
  }
};
const chartData3 = 
{
  type: 'line',
  data: {
    labels: label,
    datasets: [{
      label: "Log",
      data: log,
      borderColor: "#eb6134ff",
      fill: false,
      tension: 0,
      pointRadius: 0
    }
    ]
  }
};
window.renderChart(chartData1, this.container);
window.renderChart(chartData2, this.container);
window.renderChart(chartData3, this.container);
```

## Resources


