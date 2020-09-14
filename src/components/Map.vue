<template>
  <div id="chartdiv" ref="chartdiv"></div>
</template>

<script>
import * as am4core from "@amcharts/amcharts4/core";
import * as am4maps from "@amcharts/amcharts4/maps";
import am4geodata_worldHigh from "@amcharts/amcharts4-geodata/worldHigh";

export default {
  name: "Map",
  mounted() {
    // Create map instance
    let chart = am4core.create("chartdiv", am4maps.MapChart);

    // Set map definition
    chart.geodata = am4geodata_worldHigh;

    // Set projection
    chart.projection = new am4maps.projections.Miller();

    // Create map polygon series
    let polygonSeries = chart.series.push(new am4maps.MapPolygonSeries());

    // Make map load polygon (like country names) data from GeoJSON
    polygonSeries.useGeodata = true;

    // Configure series
    let polygonTemplate = polygonSeries.mapPolygons.template;
    polygonTemplate.tooltipText = "{name}";
    polygonTemplate.fill = am4core.color("silver");

    // Create hover state and set alternative fill color
    let hs = polygonTemplate.states.create("hover");
    hs.properties.fill = am4core.color("white");
    polygonTemplate.stroke = am4core.color("slategrey");
    chart.background.fill = am4core.color("slategrey");
    chart.background.fillOpacity = 1;
    polygonSeries.data = [
      {
        id: "CA",
        name: "Canada",
        fill: am4core.color("gold"),
      },
      {
        id: "AU",
        name: "Australia",
        fill: am4core.color("gold"),
      },
      {
        id: "MY",
        name: "Malaysia",
        fill: am4core.color("gold"),
      },
      {
        id: "SG",
        name: "Singapore",
        fill: am4core.color("gold"),
      },
      {
        id: "KR",
        name: "KR",
        fill: am4core.color("gold"),
      },
      {
        id: "TH",
        name: "Thailand",
        fill: am4core.color("gold"),
      },
      {
        id: "ID",
        name: "Indonesia",
        fill: am4core.color("gold"),
      },
      {
        id: "PH",
        name: "Philippines",
        fill: am4core.color("gold"),
      },
      {
        id: "HK",
        name: "Hong Kong",
        fill: am4core.color("gold"),
      },
      {
        id: "CN",
        name: "China",
        fill: am4core.color("gold"),
      },
      {
        id: "TW",
        name: "Taiwan",
        fill: am4core.color("gold"),
      },
      //
      // Places I want to go
      //
      {
        id: "GB",
        name: "United Kingdom",
        fill: am4core.color("skyblue"),
      },
      {
        id: "NL",
        name: "Netherlands",
        fill: am4core.color("skyblue"),
      },
      {
        id: "US",
        name: "United States",
        fill: am4core.color("skyblue"),
      },
      {
        id: "NO",
        name: "Norway",
        fill: am4core.color("skyblue"),
      },
      {
        id: "SE",
        name: "Sweden",
        fill: am4core.color("skyblue"),
      },
      {
        id: "IE",
        name: "Ireland",
        fill: am4core.color("skyblue"),
      },
      {
        id: "FR",
        name: "France",
        fill: am4core.color("skyblue"),
      },
      {
        id: "BE",
        name: "Belgium",
        fill: am4core.color("skyblue"),
      },
      {
        id: "FI",
        name: "Finland",
        fill: am4core.color("skyblue"),
      },
      {
        id: "IT",
        name: "Italy",
        fill: am4core.color("skyblue"),
      },
      {
        id: "CH",
        name: "Switzerland",
        fill: am4core.color("skyblue"),
      },
      {
        id: "NZ",
        name: "New Zealand",
        fill: am4core.color("skyblue"),
      },
    ];
    polygonSeries.exclude = ["AQ"]; // exclude antartica
    polygonTemplate.propertyFields.fill = "fill";

    // States I've Visited [Series 1]
    let stateSeries = chart.series.push(new am4maps.MapImageSeries());
    let stateSeriesTemplate = stateSeries.mapImages.template;
    let circle = stateSeriesTemplate.createChild(am4core.Circle);
    circle.radius = 4;
    circle.fill = am4core.color("hotpink");
    circle.stroke = am4core.color("black");
    circle.strokeWidth = 2;
    circle.nonScaling = true;
    circle.tooltipText = "{title}";
    stateSeriesTemplate.propertyFields.latitude = "latitude";
    stateSeriesTemplate.propertyFields.longitude = "longitude";
    stateSeries.data = [
      {
        latitude: 1.352083,
        longitude: 103.819839,
        title: "Singapore",
      },
      {
        latitude: 3.139003,
        longitude: 101.686852,
        title: "Malaysia: Kuala Lumpur",
      },
      {
        latitude: 1.4927,
        longitude: 103.7414,
        title: "Malaysia: Johor Bahru",
      },
      {
        latitude: 35.179554,
        longitude: 129.075638,
        title: "Korea: Busan",
      },
      {
        latitude: 3.4239,
        longitude: 101.7927,
        title: "Malaysia: Genting Highlands",
      },
      {
        latitude: 37.5665,
        longitude: 126.978,
        title: "Korea: Seoul",
      },
      {
        latitude: 33.489,
        longitude: 126.4983,
        title: "Seoul: Jeju Island",
      },
      {
        latitude: -37.8136,
        longitude: 144.9631,
        title: "Australia: Melbourne",
      },
      {
        latitude: 25.033,
        longitude: 121.5654,
        title: "Taiwan: Taipei",
      },
      {
        latitude: 24.1477,
        longitude: 120.6736,
        title: "Taiwan: Taichung",
      },
      {
        latitude: 22.6273,
        longitude: 120.3014,
        title: "Taiwan: Kaohsiung",
      },
      {
        latitude: 25.033,
        longitude: 121.5654,
        title: "Taiwan: Taipei",
      },
      {
        latitude: 22.3193,
        longitude: 114.1694,
        title: "Hongkong",
      },
      {
        latitude: 22.1987,
        longitude: 113.5439,
        title: "China: Macau",
      },
      {
        latitude: 13.7563,
        longitude: 100.5018,
        title: "Thailand: Bangkok",
      },
      {
        latitude: 7.8804,
        longitude: 98.3923,
        title: "Thailand: Phuket",
      },
      {
        latitude: 10.3157,
        longitude: 123.8854,
        title: "Philippines: Cebu",
      },
      {
        latitude: 14.5457,
        longitude: 121.5598,
        title: "Philippines: Real",
      },
      {
        latitude: 14.5995,
        longitude: 120.9842,
        title: "Philippines: Manila",
      },
      {
        latitude: 1.1301,
        longitude: 104.0529,
        title: "Indonesia: Batam",
      },
      {
        latitude: -8.3405,
        longitude: 115.092,
        title: "Indonesia: Bali",
      },
      {
        latitude: 43.6532,
        longitude: -79.3832,
        title: "Canada: Toronto",
      },
      {
        latitude: 45.4215,
        longitude: -75.6972,
        title: "Canada: Ottawa",
      },
    ];

    // Important Places I've Visited [Series 2]
    let starSeries = chart.series.push(new am4maps.MapImageSeries());
    let starSeriesTemplate = starSeries.mapImages.template;
    let circle2 = starSeriesTemplate.createChild(am4core.Circle);
    circle2.radius = 4;
    circle2.fill = am4core.color("white");
    circle2.stroke = am4core.color("grey");
    circle2.strokeWidth = 2;
    circle2.nonScaling = true;
    circle2.tooltipText = "{title}";
    starSeriesTemplate.propertyFields.latitude = "latitude";
    starSeriesTemplate.propertyFields.longitude = "longitude";
    starSeries.data = [
      {
        latitude: 43.0962,
        longitude: -79.0377,
        title: "Niagara Falls",
      },
    ];

    let lineSeries = chart.series.push(new am4maps.MapLineSeries());
    lineSeries.data = [
      {
        multiGeoLine: [[{ latitude: 48.856614, longitude: 2.352222 }]],
      },
    ];
    chart.zoomControl = new am4maps.ZoomControl();
  },

  beforeDestroy() {
    if (this.map) {
      this.map.dispose();
    }
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="sass" scoped>
#chartdiv
  width: 100%
  height: 90vh
</style>