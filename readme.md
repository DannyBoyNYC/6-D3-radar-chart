# Radar Weather Chart

We'll create a circular radar chart showing overall weather for the whole year

This chart will give the viewer a sense of overall weather for the whole year, and will highlight trends such as:

- What time of the year is cloudiest, and does that correlate with the coldest days?
- Do cloudy days have lower UV indices, or are they rainier?
- How does weather vary per season?

The complexity of this chart will increase the amount of time the viewer needs to wrap their head around it. But once the viewer understands it, they can answer nuanced questions.

We'll reinforce concepts we've already learned as well as introduce new concepts, such as angular math, as we build this visualization.

## Getting set up

We're going to breeze through the first four steps: accessing data, creating dimensions, drawing the canvas, and creating scales.

I've already done a few of the steps, since they should be really familiar by now: we've grabbed our data, created square dimensions, and drawn our canvas.

```js
async function drawChart() {
  // 1. Access data
  let dataset = await d3.json("./data/my_weather_data.json");

  // 2. Create chart dimensions
  const width = 600;
  let dimensions = {
    width: width,
    height: width,
    radius: width / 2,
    margin: {
      top: 120,
      right: 120,
      bottom: 120,
      left: 120,
    },
  };
  dimensions.boundedWidth =
    dimensions.width - dimensions.margin.left - dimensions.margin.right;
  dimensions.boundedHeight =
    dimensions.height - dimensions.margin.top - dimensions.margin.bottom;
  dimensions.boundedRadius =
    dimensions.radius - (dimensions.margin.left + dimensions.margin.right) / 2;

  // 3. Draw canvas
  const wrapper = d3
    .select("#wrapper")
    .append("svg")
    .attr("width", dimensions.width)
    .attr("height", dimensions.height);

  const bounds = wrapper
    .append("g")
    .style(
      "transform",
      `translate(${dimensions.margin.left}px, ${dimensions.margin.top}px)`
    );

  // 4. Create scales

  // 5. Draw data

  // 6. Draw peripherals

  // 7. Set up interactions
}

drawChart();
```
