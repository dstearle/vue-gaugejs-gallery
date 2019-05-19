<template>
    
    <div class="container">

        <div class="card bg-light">

            <h5 class="card-header">Test Component</h5>

            <div class="card-body p-5">

                 <app-test-gauge :gaugeScore="score"></app-test-gauge>

            </div>
      
        </div>

    </div>

</template>

<script>

import TestGauge from './Gauges/TestGauge.vue';

export default {

    components: {
          
        appTestGauge: TestGauge,
          
    },
    data() {
        return {
            score: 500
        }
    }
    
}

</script>