<template>

  <div class="container">

    <div class="card bg-light">

        <h5 class="card-header">Throttle Gauge</h5>

        <div class="card-body p-5">

            <div class="row align-items-center justify-content-center">

                <span ref="myGauge" class="gaugeStyle"></span>

                <canvas ref="op"></canvas>

                <!-- If you dont want to use the animated score uncomment the div below and comment out -->
                <!-- setTextField found in the initializeGraph function in methods. -->
                <!-- <div class="gaugeStyle">{{ gaugeScore }}</div> -->

            </div> 

        </div>
      
    </div>
    
  </div>

</template>

<script>

// Imports the different types of gauges from the package
// import { Gauge, Donut } from "gaugeJS/dist/gauge.min";
import { Gauge } from "gaugeJS/dist/gauge.min";

export default {

  props: {

    gaugeScore: {
      type: Number,
      default: 35
    },
    
  },
  data() {

    return {
        
      opts: {
          angle: 0.1, // The span of the gauge arc
          lineWidth: 0.3, // The line thickness
          radiusScale: 1, // Relative radius
          pointer: {
            length: 0.5, // Relative to gauge radius
            strokeWidth: 0.035, // The thickness
            color: "#000000" // Fill color
          },
          limitMax: false, // If false, max value increases automatically if value > maxValue
          limitMin: false, // If true, the min value of the gauge will be fixed
          colorStart: "#6FADCF",
          colorStop: "#e0274a", // The color of the bar in the gauge
          strokeColor: "#E0E0E0", // The color of the background in the gauge
          generateGradient: true,
          highDpiSupport: true, // High resolution support
          // renderTicks is Optional
          renderTicks: {
              divisions: 5,
              divWidth: 0.6,
              divLength: .2,
              divColor: '#333333',
              subDivisions: 9,
              subLength: 0.2,
              subWidth: 0.6,
              subColor: '#666666'
         },
         // Sets the labels for the ticks
        //  staticLabels: {
        //      font: "10px sans-serif",  // Specifies font
        //      labels: [0, 20, 40, 60, 80, 100],  // Print labels at these values
        //      color: "#000000",  // Optional: Label text color
        //      fractionDigits: 0  // Optional: Numerical precision. 0=round off.
        // },
         // Sets the colors and height for the different sections of the gauge
         staticZones: [
            {strokeStyle: "#15a15f", min: 0, max: 20, height: 1.4}, // Green
            {strokeStyle: "#8fb92f", min: 20, max: 40, height: 1.2}, // Light Green
            {strokeStyle: "#ffc107", min: 40, max: 60, height: 1}, // Yellow
            {strokeStyle: "#ff792a", min: 60, max: 80, height: 0.8}, // Orange
            {strokeStyle: "#e0274a", min: 80, max: 100, height: 0.6}  // Red
        ],
          
      }
    
    };

  },
  mounted() {
    this.initializeGauge();
  },
  watch: {
    // Checks for new value for gaugeScore
    gaugeScore: function(newVal) {
      this.gauge.set(newVal);
    },
  },
  methods: {
    // Creates the graph to be rendered
    initializeGauge() {
        this.gauge = new Gauge(this.$refs.op); // Sets the type of guage you wish to use (Gauge, Donut)
        this.gauge.maxValue = 100; // set max gauge value
        this.gauge.setMinValue(0); // Prefer setter over gauge.minValue = 0
        this.gauge.animationSpeed = 32; // set animation speed (32 is default value)
        this.gauge.setOptions(this.opts);

        // Sets the animated score into the text field
        // this.gauge.setTextField(
        //     this.$refs['myGauge'],
        //     this.decimalPlace
        // );

        this.gauge.set(this.gaugeScore); // Sets the value for both the gauge bar and the displayed score
    },

  },

};

</script>

<style scoped>

.gaugeStyle {
    position: absolute;
    text-align: center;
    left: 0;
    right: 0;
}

.gaugeStyle2 {
    position: absolute;
    text-align: center;
    left: 0;
    right: 0;
}

</style>