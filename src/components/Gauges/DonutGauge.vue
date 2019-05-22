<template>

  <div class="container">

    <div class="card bg-light">

        <h5 class="card-header">Donut Gauge</h5>

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
import { Donut } from "gaugeJS/dist/gauge.min";

export default {

  props: {

    gaugeScore: {
      type: Number,
      default: 300
    },
    
  },
  data() {

    return {
        
      opts: {
          angle: 0.1, // The span of the gauge arc
          lineWidth: 0.1, // The line thickness
          radiusScale: 1, // Relative radius
          pointer: {
            length: 0.6, // Relative to gauge radius
            strokeWidth: 0.035, // The thickness
            color: "#000000" // Fill color
          },
          limitMax: false, // If false, max value increases automatically if value > maxValue
          limitMin: false, // If true, the min value of the gauge will be fixed
          colorStart: "#6FADCF",
          colorStop: "#e0274a", // The color of the bar in the gauge
          strokeColor: "#E0E0E0", // The color of the background in the gauge
          generateGradient: true,
          highDpiSupport: true // High resolution support
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
        this.gauge = new Donut(this.$refs.op); // Sets the type of guage you wish to use (Gauge, Donut)
        this.gauge.maxValue = 500; // set max gauge value
        this.gauge.setMinValue(0); // Prefer setter over gauge.minValue = 0
        this.gauge.animationSpeed = 32; // set animation speed (32 is default value)
        this.gauge.setOptions(this.opts);

        // Sets the animated score into the text field
        this.gauge.setTextField(
            this.$refs['myGauge'],
            this.decimalPlace
        );

        this.gauge.set(this.gaugeScore); // Sets the value for both the gauge bar and the displayed score
    },
    // Determines color of the bar for the gauge
    gaugeColor() {
        if(this.gaugeScore >= 400) {
            this.opts.colorStop = '#15a15f';
            this.initializeGauge();
            // console.log("test1")
            // console.log(this.opts.colorStop)
        }
        else if(this.gaugeScore < 400 && this.gaugeScore > 249) {
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