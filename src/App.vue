<template>
   
    <div class="container">
       
        <div class="row">
           
            <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
               
                <h1>Vue GaugeJS Gallery</h1>
                
                <hr>

                  <br>

                <app-test-component></app-test-component>

                  <br>

                <app-donut-gauge></app-donut-gauge>

                  <br>

                <app-regular-gauge></app-regular-gauge>

                  <br>

                <app-section-gauge></app-section-gauge>

                  <br>

                <app-throttle-gauge></app-throttle-gauge>
                                
            </div>
            
        </div>
        
    </div>
    
</template>

<script>

  import TestComponent from "./components/TestComponent.vue";
  import DonutGauge from "./components/Gauges/DonutGauge.vue";
  import RegularGauge from "./components/Gauges/RegularGauge.vue";
  import SectionGauge from "./components/Gauges/SectionGauge.vue";
  import ThrottleGauge from "./components/Gauges/ThrottleGauge.vue";
    
  export default {
      
      components: {
          
          appTestComponent: TestComponent,
          appDonutGauge: DonutGauge,
          appRegularGauge: RegularGauge,
          appSectionGauge: SectionGauge,
          appThrottleGauge: ThrottleGauge
          
      },

  }
    
</script>

<style>
    
    body {
        
        padding: 30px;
        
    }

</style>
