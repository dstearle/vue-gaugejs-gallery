<template>

  <div class="container">

    <div class="card bg-light">

      <h5 class="card-header">Regular Gauge</h5>

      <div class="col card-body p-5">

        <div class="row align-items-center justify-content-center">

          <span ref="myGauge" class="gaugeStyle"></span>

          <canvas ref="op"></canvas>

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
          angle: 0, // The span of the gauge arc
          lineWidth: 0.44, // The line thickness
          radiusScale: 1, // Relative radius
          pointer: {
            length: 0.6, // Relative to gauge radius
            strokeWidth: 0.035, // The thickness
            color: "#000000" // Fill color
          },
          limitMax: false, // If false, max value increases automatically if value > maxValue
          limitMin: false, // If true, the min value of the gauge will be fixed
          colorStart: "#6FADCF",
          colorStop: "#ffc107", // The color of the bar in the gauge
          strokeColor: "#E0E0E0", // The color of the background in the gauge
          generateGradient: true,
          highDpiSupport: true, // High resolution support
          // renderTicks is Optional
        //   renderTicks: {
        //       divisions: 5,
        //       divWidth: 1.1,
        //       divLength: 0.5,
        //       divColor: '#333333',
        //       subDivisions: 3,
        //       subLength: 0.5,
        //       subWidth: 0.6,
        //       subColor: '#666666'
        //  },
         // Sets the labels for the ticks
        //  staticLabels: {
        //      font: "10px sans-serif",  // Specifies font
        //      labels: [0, 20, 40, 60, 80, 100],  // Print labels at these values
        //      color: "#000000",  // Optional: Label text color
        //      fractionDigits: 0  // Optional: Numerical precision. 0=round off.
        // },
         // Sets the colors for the different sections of the gauge
        //  staticZones: [
        //     {strokeStyle: "#e0274a", min: 0, max: 20}, // Red
        //     {strokeStyle: "#ff792a", min: 20, max: 40}, // Orange
        //     {strokeStyle: "#ffc107", min: 40, max: 60}, // Yellow
        //     {strokeStyle: "#8fb92f", min: 60, max: 80}, // Light Green
        //     {strokeStyle: "#15a15f", min: 80, max: 100}  // Green
        // ],
          
      }
    
    };

  },
  mounted() {
    this.initializeGauge();
    this.gaugeColor();
  },
  watch: {
    // Checks for new value for gaugeScore
    gaugeScore: function(newVal) {
      this.gauge.set(newVal);
      this.gaugeColor();
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
    // Determines color of the bar for the gauge
    gaugeColor() {
      if(this.gaugeScore >= 80) {
        this.opts.colorStop = '#15a15f';
        this.initializeGauge();
        // console.log("test1")
        // console.log(this.opts.colorStop)
      }
      else if(this.gaugeScore < 80 && this.gaugeScore > 50) {
        this.opts.colorStop = '#ffc107';
        this.initializeGauge();
        // console.log("test2")
        // console.log(this.opts.colorStop)
      }
      else{
        this.opts.colorStop = ('#e0274a');
        this.initializeGauge();
        // console.log("test3")
        // console.log(this.opts.colorStop)
      }
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

</style>