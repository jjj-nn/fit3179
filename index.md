{
  "$schema": "https://vega.github.io/schema/vega-lite/v5.json",
  "width": 600,
  "height": 300,
  "data": {
    "url": "https://raw.githubusercontent.com/jjj-nn/fit3179/main/simplifiedaust.json",
    "format": {"type": "topojson", "feature": "STE_2016_AUST"}
  },
  "transform": [
    {
      "lookup": "properties.STE_NAME16",
      "from": {
        "data": {
          "url": "https://raw.githubusercontent.com/jjj-nn/fit3179/main/percentjulyonly.csv"
        },
        "key": "State",
        "fields": ["Percentage Change"]
      }
    }
  ],
  "projection": {"type": "equirectangular"},
  "mark": "geoshape",
  "encoding": {
    "color": {
      "field": "Percentage Change",
      "type": "quantitative",
      "scale": {
        "type": "threshold",
        "domain": [-99.5, -99, -95, -90, -85, -80],
        "range": [
          "#662506",
          "#993404",
          "#cc4c02",
          "#ec7014",
          "#fe9929",
          "#fee391"
        ]
      }
    },
    "tooltip": [
      {"field": "properties.STE_NAME16", "type": "nominal", "title": "State"},
      {"field": "Percentage Change", "type": "quantitative"}
    ]
  }
}
