
# Understanding Plotly

### Learning Objectives

* Understand the iplot method
* Understand how to create different traces/plots like a scatter plot, or a line plot
* Understand how to have a chart with multiple traces

### Introduction

As you've seen in recent lessons, data science leans on data visualizations to draw inferences about our data, and to make sense of the math we use in making sense of this data.  We saw how plotting data can display the relationship between x and y variables and how the impact that changing the y-intercept or slope variable has on a regression line.  

In this lesson, let's explore the Plotly library, which allows us to create data visualizations with Python.  As we do so, pay careful attention to the data type that our methods require: whether they are dictionaries or arrays, or arrays of dictionaries.  Ok, let's go!

### Working through a linear regression 

To get started with plotly first install the library on your computer.  You can do so in Jupyter through executing the cell below.


```python
!pip install plotly
```


```python
def add(number):
    return number + 1
```


```python
add(1) # 2
```

If plotly is already on your computer, pip will tell you that the require is already satisfied.  That's ok - nothing broke.

The next step is to import the plotly library. 


```python
import plotly
from plotly.offline import iplot, init_notebook_mode
init_notebook_mode(connected=True)
```


<script>requirejs.config({paths: { 'plotly': ['https://cdn.plot.ly/plotly-latest.min']},});if(!window.Plotly) {{require(['plotly'],function(plotly) {window.Plotly=plotly;});}}</script>


If we plot offline, we do not need to provide a login.  So we do so, while plotting our first plot with the below line.


```python
plotly.offline.iplot([
    {}
])
```


<div id="33e2c690-541b-4247-a9fb-449854ef9c16" style="height: 525px; width: 100%;" class="plotly-graph-div"></div><script type="text/javascript">require(["plotly"], function(Plotly) { window.PLOTLYENV=window.PLOTLYENV || {};window.PLOTLYENV.BASE_URL="https://plot.ly";Plotly.newPlot("33e2c690-541b-4247-a9fb-449854ef9c16", [{}], {}, {"showLink": true, "linkText": "Export to plot.ly"})});</script>


Let's take another look at that line of code.
```python
plotly.offline.iplot([
    {}
])
```

We reference the `plotly` library, which we imported above.  Then to the `iplot` method we pass an array, which has a dictionary in it.  That dictionary can represent a scatter chart, a line chart, or other types of charts.  Another name for these charts is traces.  We'll use the two words interchangeably.  We pass the dictionary into an array because we can have more then one chart in the same graph - for example a scatter plot underneath a line plot.  

Now, for the dictionary that represents a chart, we should begin to provide some information.  We can do so by giving our plot some data.  Below we plot four points.  Notice that we provide the x and y coordinates in two separate attributes of the dictionary.  Change around the data to get a feel for how it works.


```python
trace = {'x': [1, 2, 3, 4], 'y': [1, 2, 3, 4]}

plotly.offline.iplot([
    trace
])
```


<div id="ddc1fd41-5a0d-486a-9b64-a5b284df490f" style="height: 525px; width: 100%;" class="plotly-graph-div"></div><script type="text/javascript">require(["plotly"], function(Plotly) { window.PLOTLYENV=window.PLOTLYENV || {};window.PLOTLYENV.BASE_URL="https://plot.ly";Plotly.newPlot("ddc1fd41-5a0d-486a-9b64-a5b284df490f", [{"x": [1, 2, 3, 4], "y": [1, 2, 3, 4]}], {}, {"showLink": true, "linkText": "Export to plot.ly"})});</script>


The line above produces a line chart.  However this is just the default.  We can change it by changing the mode to `markers`.  Let's also change the color of the markers while we are at it.  


```python
trace = {'x': [1, 2, 3, 4], 'y': [1, 2, 3, 4], 'mode': 'markers', 'marker': {'color': 'rgba(255, 182, 193, .9)'}}

plotly.offline.iplot([
    trace
])
```


<div id="186c1747-18bb-4eee-b04c-5ed8fdfcb65f" style="height: 525px; width: 100%;" class="plotly-graph-div"></div><script type="text/javascript">require(["plotly"], function(Plotly) { window.PLOTLYENV=window.PLOTLYENV || {};window.PLOTLYENV.BASE_URL="https://plot.ly";Plotly.newPlot("186c1747-18bb-4eee-b04c-5ed8fdfcb65f", [{"x": [1, 2, 3, 4], "y": [1, 2, 3, 4], "mode": "markers", "marker": {"color": "rgba(255, 182, 193, .9)"}}], {}, {"showLink": true, "linkText": "Export to plot.ly"})});</script>


Now remember we said that we can add more than one trace to a given graph.  Let's do that now.  We'll keep the first trace largely the same by using the same data, and color of markers.  We'll add a name to our trace of 'Some dots', simply by adding a name attribute.

In the second trace, we have some new data, and set the color as blue.  Because we did not specify a mode, it defaults to connecting the points as a line.  And we name our trace as "Our nice line".   

Then, we set a variable `initial_sample_budgets` equal to a list of our budgets.  


```python
trace0 = {'x': [1, 2, 3, 4], 'y': [1, 2, 3, 4], 'mode': 'markers', 'marker': {'color': 'rgba(255, 182, 193, .9)'}, 'name': 'Some dots'}
trace1 = {'x': [1.5, 2.5, 3.5, 4.5], 'y': [3, 5, 7, 9], 'marker': {'color': 'blue'}, 'name': 'Our nice line'}

plotly.offline.iplot([
    trace0, trace1
])
```


<div id="731b3213-d23e-46c1-b2d5-b3c5132c016b" style="height: 525px; width: 100%;" class="plotly-graph-div"></div><script type="text/javascript">require(["plotly"], function(Plotly) { window.PLOTLYENV=window.PLOTLYENV || {};window.PLOTLYENV.BASE_URL="https://plot.ly";Plotly.newPlot("731b3213-d23e-46c1-b2d5-b3c5132c016b", [{"x": [1, 2, 3, 4], "y": [1, 2, 3, 4], "mode": "markers", "marker": {"color": "rgba(255, 182, 193, .9)"}, "name": "Some dots"}, {"x": [1.5, 2.5, 3.5, 4.5], "y": [3, 5, 7, 9], "marker": {"color": "blue"}, "name": "Our nice line"}], {}, {"showLink": true, "linkText": "Export to plot.ly"})});</script>


### Working with types

So far, we have only worked with either scatter charts or line charts.  The two charts are really quite similar -- line charts connect points with a line -- and plotly treats them as such.  There are other types of charts.

We can make a bar chart, for example, simply by specifying the in our dictionary that the type is a bar chart.


```python
trace0 = {'type': 'bar', 'x': ['bobby', 'susan', 'eli', 'malcolm'], 'y': [3, 5, 7, 9], 'marker': {'color': 'blue'}, 'name': 'Our nice line'}

plotly.offline.iplot([
    trace0
])
```


<div id="6eb198ba-55c5-4494-8fe2-e8469bb95234" style="height: 525px; width: 100%;" class="plotly-graph-div"></div><script type="text/javascript">require(["plotly"], function(Plotly) { window.PLOTLYENV=window.PLOTLYENV || {};window.PLOTLYENV.BASE_URL="https://plot.ly";Plotly.newPlot("6eb198ba-55c5-4494-8fe2-e8469bb95234", [{"type": "bar", "x": ["bobby", "susan", "eli", "malcolm"], "y": [3, 5, 7, 9], "marker": {"color": "blue"}, "name": "Our nice line"}], {}, {"showLink": true, "linkText": "Export to plot.ly"})});</script>


Now another way to create a bar chart is to use the constructor provided by plotly.  It's not too bad.  First, we import our graph_objs library from plotly.  And then we call the bar chart constructor. 


```python
from plotly import graph_objs 

bar_chart = graph_objs.Bar(
            x=['bobby', 'susan', 'eli', 'malcolm'],
            y=[3, 5, 7, 9]
    )

bar_chart
```




    {'type': 'bar', 'x': ['bobby', 'susan', 'eli', 'malcolm'], 'y': [3, 5, 7, 9]}



We refer to `graph_objs.Bar` as a constructor because it literally constructs python dictionaries with a key of `type` that equals `bar`.  Then, we can pass this dictionary to our `iplot` method to display our bar chart.


```python
bar_chart = graph_objs.Bar(
            x=['bobby', 'susan', 'eli', 'malcolm'],
            y=[3, 5, 7, 9]
    )


plotly.offline.iplot([
    trace0
])
```


<div id="1cfd5415-344c-4b79-957b-892163c4b237" style="height: 525px; width: 100%;" class="plotly-graph-div"></div><script type="text/javascript">require(["plotly"], function(Plotly) { window.PLOTLYENV=window.PLOTLYENV || {};window.PLOTLYENV.BASE_URL="https://plot.ly";Plotly.newPlot("1cfd5415-344c-4b79-957b-892163c4b237", [{"type": "bar", "x": ["bobby", "susan", "eli", "malcolm"], "y": [3, 5, 7, 9], "marker": {"color": "blue"}, "name": "Our nice line"}], {}, {"showLink": true, "linkText": "Export to plot.ly"})});</script>


There are constructors for making other charts as well.  


```python
graph_objs.Scatter()
```




    {'type': 'scatter'}




```python
graph_objs.Pie()
```




    {'type': 'pie'}



And of course, we can always use the dictionary constructor to create our dictionaries.


```python
pie_trace = dict(type="pie", labels=["chocolate", "vanilla", "strawberry"], values=[10, 5, 15])

plotly.offline.iplot([
    pie_trace
])
```


<div id="464546ec-26b8-45fc-85dd-2778fbb02ee4" style="height: 525px; width: 100%;" class="plotly-graph-div"></div><script type="text/javascript">require(["plotly"], function(Plotly) { window.PLOTLYENV=window.PLOTLYENV || {};window.PLOTLYENV.BASE_URL="https://plot.ly";Plotly.newPlot("464546ec-26b8-45fc-85dd-2778fbb02ee4", [{"type": "pie", "labels": ["chocolate", "vanilla", "strawberry"], "values": [10, 5, 15]}], {}, {"showLink": true, "linkText": "Export to plot.ly"})});</script>


### Modifying a Chart Layout

So far we have seen how to specify attributes of traces or charts, which display our data.  Now let's see how to modify the overall layout in our chart.

Note that the format of our traces will not change.


```python
trace_of_data = {'x': [1.5, 2.5, 3.5, 4.5], 'y': [3, 5, 7, 9], 'marker': {'color': 'blue'}, 'name': 'Our nice line'}

# plotly.offline.iplot([
#     trace_of_data
# ])
```

However, instead of passing to our `iplot` function an array of traces, we pass a dictionary with a `data` key, which has a value of an array of traces.  And a `layout` key, with a value of a dictionary representing our layout.


```python
layout = {'title': 'Scatter Plot'}
trace_of_data = {'x': [1.5, 2.5, 3.5, 4.5], 'y': [3, 5, 7, 9], 'marker': {'color': 'blue'}, 'name': 'Our nice line'}

figure = {'data': [trace_of_data], 'layout': layout}

plotly.offline.iplot(figure)
```


<div id="e2ea24c8-2bb1-400a-b608-134f969cb7a4" style="height: 525px; width: 100%;" class="plotly-graph-div"></div><script type="text/javascript">require(["plotly"], function(Plotly) { window.PLOTLYENV=window.PLOTLYENV || {};window.PLOTLYENV.BASE_URL="https://plot.ly";Plotly.newPlot("e2ea24c8-2bb1-400a-b608-134f969cb7a4", [{"x": [1.5, 2.5, 3.5, 4.5], "y": [3, 5, 7, 9], "marker": {"color": "blue"}, "name": "Our nice line"}], {"title": "Scatter Plot"}, {"showLink": true, "linkText": "Export to plot.ly"})});</script>


Now above we only used the `layout` to specify our chart's title.  Let's now also use it to add a range to our x axis and y axis.  Currently, we are allowing plotly to automatically set our range.  But we can also specify this.  Let's change it so that the x and y axis both have the same range.


```python
layout = {'title': 'Scatter Plot', 'xaxis': {'range': [1, 10]}, 'yaxis': {'range': [1, 10]}}
trace_of_data = {'x': [1.5, 2.5, 3.5, 4.5], 'y': [3, 5, 7, 9], 'marker': {'color': 'blue'}, 'name': 'Our nice line'}

figure = {'data': [trace_of_data], 'layout': layout}

plotly.offline.iplot(figure)
```


<div id="4c44a14e-dacc-4d3b-be02-404b59a90f02" style="height: 525px; width: 100%;" class="plotly-graph-div"></div><script type="text/javascript">require(["plotly"], function(Plotly) { window.PLOTLYENV=window.PLOTLYENV || {};window.PLOTLYENV.BASE_URL="https://plot.ly";Plotly.newPlot("4c44a14e-dacc-4d3b-be02-404b59a90f02", [{"x": [1.5, 2.5, 3.5, 4.5], "y": [3, 5, 7, 9], "marker": {"color": "blue"}, "name": "Our nice line"}], {"title": "Scatter Plot", "xaxis": {"range": [1, 10]}, "yaxis": {"range": [1, 10]}}, {"showLink": true, "linkText": "Export to plot.ly"})});</script>


### Summary

In this section we saw how we can use Plotly's library to create data visualisations.  We create different traces to represent our data, with each trace represented as a dictionary which is passed to our `iplot` method.  We saw we can have multiple traces displayed in the chart, as the traces are wrapped in an array.  We saw that even when we use constructors like `graph_objs.Bar` to create a chart, all this does is create a dictionary which is then passed to our `iplot` method.  Then we moved onto modifying our layout for our charts, which is also just a python dictionary.  


```python

```