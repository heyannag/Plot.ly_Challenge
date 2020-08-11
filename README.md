# Plotly Challenge - [Belly Button Biodiversity Interactive Dashboard](https://heyannag.github.io/Plot.ly_Challenge/)

## Process Overview:

Project focus was to build an interactive dashboard to explore a data set in JSON. The data set is from a science project called [Belly Button Biodiversity](http://robdunnlab.com/projects/belly-button-biodiversity/results-and-data/). 
This project was developed in JavaScript using Plotly.JS and D3.JS.

* The IDs are selected dynamically from the data set from [JSON file](/JS/data/samples.json).<br>
![doc](/images/select_ID.png)<br>

# Technologies:
* JavaScript
  * D3.js
  * Plotly.js
* HTML and CSS3
-----------
As seen below, a D3 function was created to process the JSON file and extract the IDs to correspond with the HTML page.
<br>
```JavaScript
function init() {
  d3.json("JS/data/samples.json").then(dataInitial => {
    data = dataInitial;
    var selectValues = dataInitial.names;

    var selectOpt = d3.select("#selDataset");

    selectValues.forEach(value => {
      selectOpt
        .append("option")
        .text(value)
        .attr("value", function() {
          return value;
        });
    });
  });
}
```

* Panel that shows information based on the selected ID<br>
![panel](/images/panel.png) <br>
```JavaScript
function panelPlot(valueSelect) {
  //   console.log(valueSelect);
  var filterValue = data.metadata.filter(value => value.id == valueSelect);

  var divValue = d3.select(".panel-body");
  divValue.html("");
  divValue.append("p").text(`id: ${filterValue[0].id}`);
  divValue.append("p").text(`ethnicity: ${filterValue[0].ethnicity}`);
  divValue.append("p").text(`gender: ${filterValue[0].gender}`);
  divValue.append("p").text(`age: ${filterValue[0].age}`);
  divValue.append("p").text(`location: ${filterValue[0].location}`);
  divValue.append("p").text(`bbtype: ${filterValue[0].bbtype}`);
  divValue.append("p").text(`wfreq: ${filterValue[0].wfreq}`);
}
```
* Horizontal Bar with descending(reversed) values based on selected data<br>
![hbar](/images/horizontal_bar.png) <br>
```JavaScript
function demographicFunc(valueSelect) {
...
}
```
* Bubble chart based on selected data<br>
![hbar](/images/bubble_chart.png) <br>
```JavaScript
function bubbleChart(valueSelect) {
...
}
```

* Gauge chart based on selected data<br>
![gauge](/images/gauge_chart.png) <br>
```JavaScript
function gaugeChart(valueSelect) {
...
}
```

