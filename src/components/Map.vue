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
    let WINDOW_WIDTH = window.innerWidth;

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
    polygonTemplate.fill = am4core.color("whitesmoke");

    // Create hover state and set alternative fill color
    let hs = polygonTemplate.states.create("hover");
    hs.properties.fill = am4core.color("white");
    polygonTemplate.stroke = am4core.color("slategrey");
    chart.background.fill = am4core.color("slategrey");
    chart.background.fillOpacity = 1;
    polygonSeries.data = [
      {
        id: "CA",
        name: "Canada: April 2013",
        fill: am4core.color("gold"),
      },
      {
        id: "AU",
        name: "Australia: December 2016",
        fill: am4core.color("gold"),
      },
      {
        id: "MY",
        name: "Malaysia",
        fill: am4core.color("gold"),
      },
      {
        id: "SG",
        name: "Singapore: Home",
        fill: am4core.color("gold"),
      },
      {
        id: "KR",
        name: "Korea: July 2017",
        fill: am4core.color("gold"),
      },
      {
        id: "TH",
        name: "Thailand: October 2014",
        fill: am4core.color("gold"),
      },
      {
        id: "ID",
        name: "Indonesia: June 2015",
        fill: am4core.color("gold"),
      },
      {
        id: "PH",
        name: "Philippines: November 2018",
        fill: am4core.color("gold"),
      },
      {
        id: "HK",
        name: "Hong Kong: January 2014",
        fill: am4core.color("gold"),
      },
      {
        id: "CN",
        name: "China: January 2014",
        fill: am4core.color("gold"),
      },
      {
        id: "TW",
        name: "Taiwan: October 2015",
        fill: am4core.color("gold"),
      },
      // Europe 2022 Update
      {
        id: "GB",
        name: "United Kingdom: May 2022",
        fill: am4core.color("gold"),
      },
      {
        id: "FR",
        name: "France: May 2022",
        fill: am4core.color("gold"),
      },
      {
        id: "BE",
        name: "Belgium: May 2022",
        fill: am4core.color("gold"),
      },
      {
        id: "CH",
        name: "Switzerland: April 2022",
        fill: am4core.color("gold"),
      },
      {
        id: "NL",
        name: "Netherlands: April 2022",
        fill: am4core.color("gold"),
      },
      {
        id: "DE",
        name: "Germany: March 2022",
        fill: am4core.color("gold"),
      },
      //
      // Places I want to go
      //

      {
        id: "NZ",
        name: "New Zealand",
        fill: am4core.color("palegreen"),
      },
      {
        id: "KP",
        name: "North Korea",
        fill: am4core.color("palegreen"),
      },
      {
        id: "NP",
        name: "Nepal",
        fill: am4core.color("palegreen"),
      },
      {
        id: "MM",
        name: "Myanmmar",
        fill: am4core.color("palegreen"),
      },
      {
        id: "LA",
        name: "Laos",
        fill: am4core.color("palegreen"),
      },
      {
        id: "KH",
        name: "Cambodia",
        fill: am4core.color("palegreen"),
      },
      {
        id: "VN",
        name: "Vietnam",
        fill: am4core.color("palegreen"),
      },
      // Places I want to go eventually
      {
        id: "US",
        name: "United States",
        fill: am4core.color("palegreen"),
      },
      {
        id: "NO",
        name: "Norway",
        fill: am4core.color("palegreen"),
      },
      {
        id: "SE",
        name: "Sweden",
        fill: am4core.color("palegreen"),
      },
      {
        id: "IE",
        name: "Ireland",
        fill: am4core.color("palegreen"),
      },
      {
        id: "FI",
        name: "Finland",
        fill: am4core.color("palegreen"),
      },
      {
        id: "IT",
        name: "Italy",
        fill: am4core.color("palegreen"),
      },

      {
        id: "IN",
        name: "India",
        fill: am4core.color("palegreen"),
      },
      {
        id: "ES",
        name: "Spain",
        fill: am4core.color("palegreen"),
      },
      {
        id: "GR",
        name: "Greece",
        fill: am4core.color("palegreen"),
      },
      {
        id: "TR",
        name: "Turkey",
        fill: am4core.color("palegreen"),
      },
      {
        id: "DK",
        name: "Denmark",
        fill: am4core.color("palegreen"),
      },
      {
        id: "MN",
        name: "Mongolia",
        fill: am4core.color("palegreen"),
      },
    ];
    polygonSeries.exclude = ["AQ"]; // exclude antartica
    polygonTemplate.propertyFields.fill = "fill";

    // States I've Visited [Series 1]
    let stateSeries = chart.series.push(new am4maps.MapImageSeries());
    let stateSeriesTemplate = stateSeries.mapImages.template;
    let circle = stateSeriesTemplate.createChild(am4core.Circle);
    circle.radius = 4;
    circle.fill = am4core.color("turquoise");
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
      // Europe 2022 Update
      {
        latitude: 48.1351,
        longitude: 11.582,
        title: "Munich: 31 March 2022",
      },
      {
        latitude: 48.779301,
        longitude: 9.1071758,
        title: "Stuttgart: 6 April 2022",
      },
      {
        latitude: 48.5222366,
        longitude: 8.977744,
        title: "Tubingen: 11 April 2022",
      },
      {
        latitude: 47.7153074,
        longitude: 8.6108257,
        title: "Schaffhausen: 12 April 2022",
      },
      {
        latitude: 48.5691668,
        longitude: 7.6920399,
        title: "Strasbourg: 14 April 2022",
      },
      {
        latitude: 52.3547498,
        longitude: 4.8339211,
        title: "Amsterdam: 15 April 2022 - King's Day: 26 April",
      },
      {
        latitude: 48.8589466,
        longitude: 2.2769956,
        title: "Paris: 28 April 2022",
      },
      {
        latitude: 51.2608697,
        longitude: 3.1520689,
        title: "Paris: 7 May 2022",
      },
      {
        latitude: 52.450318,
        longitude: 4.7880663,
        title: "Zaandam: 8 May 2022",
      },
      {
        latitude: 55.9412211,
        longitude: -3.3488579,
        title: "Edinburgh: 12 May 2022",
      },
      {
        latitude: 51.7548197,
        longitude: -1.2565555,
        title: "Oxford: 19 May 2022",
      },
      {
        latitude: 51.528505,
        longitude: -0.3886615,
        title: "London: 22 May 2022",
      },
      // Europe Minor Cities
      {
        latitude: 47.5729138,
        longitude: 9.6535152,
        title: "Lindau: 12 April 2022",
      },
      {
        latitude: 47.9874048,
        longitude: 7.7263807,
        title: "Freiburg im Breisgau: 13 April 2022",
      },
      {
        latitude: 52.071739,
        longitude: 4.254228,
        title: "The Hague: 23 April 2022",
      },
      {
        latitude: 51.4839234,
        longitude: -0.6140359,
        title: "Windsor: 29 May 2022",
      },
      {
        latitude: 51.3801748,
        longitude: -2.3995493,
        title: "Bath: 29 May 2022",
      },
      {
        latitude: 51.5548788,
        longitude: -0.3162035,
        title: "Wembly: 1 June 2022 - Finalissima: Argentina vs Italy",
      },
      {
        latitude: 51.3328806,
        longitude: -0.297906,
        title: "Epsom: 4 June 2022",
      },
      {
        latitude: 51.400526,
        longitude: -0.3440538,
        title: "Molesey: 5 June 2022",
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
        title: "Niagara Falls: April 2013",
      },
      {
        latitude: 57.2741432,
        longitude: -4.6417654,
        title: "Loch Ness: 14 May 2022",
      },
      {
        latitude: 51.1788853,
        longitude: -1.8284037,
        title: "Stonehenge: 29 May 2022",
      },
    ];

    chart.zoomControl = new am4maps.ZoomControl();
    if (WINDOW_WIDTH < 453) {
      chart.homeZoomLevel = 4;
      chart.homeGeoPoint = {
        latitude: 1,
        longitude: 103,
      };
    } else if (WINDOW_WIDTH < 768) {
      chart.homeZoomLevel = 3;
      chart.homeGeoPoint = {
        latitude: 1,
        longitude: 103,
      };
    } else if (WINDOW_WIDTH < 991) {
      chart.homeZoomLevel = 2;
      chart.homeGeoPoint = {
        latitude: 1,
        longitude: 103,
      };
    } else if (WINDOW_WIDTH < 1200) {
      chart.homeZoomLevel = 1.5;
      chart.homeGeoPoint = {
        latitude: 1,
        longitude: 103,
      };
    }
    chart.zoomControl.valign = "middle";
    // Legend
    let legend = new am4maps.Legend();

    legend.parent = chart.chartContainer;
    legend.background.fill = am4core.color("#fff");
    legend.background.fillOpacity = 0.2;
    legend.color = am4core.color("#fff");
    legend.width = 210;
    legend.position = "left";
    legend.padding(10, 15, 10, 15);
    legend.data = [
      {
        name: "Visited",
        fill: "gold",
      },
      {
        name: "To Visit",
        fill: "palegreen",
      },
      {
        name: "Cities / States",
        fill: "turquoise",
      },
      {
        name: "Points of Interest",
        fill: "white",
      },
    ];
    legend.itemContainers.template.clickable = false;
    legend.itemContainers.template.focusable = false;
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
  height: 100vh
</style>
