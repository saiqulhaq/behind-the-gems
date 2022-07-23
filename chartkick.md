Gem link: https://github.com/ankane/chartkick  
This note is based on this commit https://github.com/ankane/chartkick/commit/0b208b295dca82d6a6ec7ac706e3773ba18684d2

# Summary

This gem will generate javascript code, `new Chartkick......` and injects it into the Rails view  

# What I learned

1. It has #chart_json function on Enumerable module
it's to convert any object to json, to comply with [chartkick.js](https://github.com/ankane/chartkick.js) format, which are like these

```javascript
new Chartkick.LineChart("chart-1", {"2021-01-01": 11, "2021-01-02": 6})
```

Pie chart

```javascript
new Chartkick.PieChart("chart-1", [["Blueberry", 44], ["Strawberry", 23]])
```

Column chart

```javascript
new Chartkick.ColumnChart("chart-1", [["Sun", 32], ["Mon", 46], ["Tue", 28]])
```

2. All the Rails Helpers are just decorator

This gem actually is a bridge, it translate our Ruby code to be Javascript code
all the hard work is done by chartkick.js  
that's why the gem has a few Ruby files only.  
Following is the example

```ruby
def line_chart(data_source, **options)
  chartkick_chart "LineChart", data_source, **options
end

def pie_chart(data_source, **options)
  chartkick_chart "PieChart", data_source, **options
end

def column_chart(data_source, **options)
  chartkick_chart "ColumnChart", data_source, **options
end
```

---
**NOTE**

`**options` is a new operator introduced in Ruby 2.0, it captures all **keywords arguments**. Ref https://stackoverflow.com/questions/18289152/what-does-a-double-splat-operator-do

---
