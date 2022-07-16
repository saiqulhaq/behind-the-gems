Gem link: https://github.com/ankane/chartkick  
This note is based on this commit https://github.com/ankane/chartkick/commit/0b208b295dca82d6a6ec7ac706e3773ba18684d2

# What I learned

### It has #chart_json function on Enumerable module
it's to convert any object to json, to comply with chart.js format

and it seems every chart should be on following format

```ruby
[
  {
    data: 12
  },
  {
    data: 123
  }
]
```

### Rails Helpers

The main goal of this gem is providing easy rails helpers to render the chart
