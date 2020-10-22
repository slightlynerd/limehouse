<template>
  <div id="app">
    <div class="row justify-between navbar">
      <img src="@/assets/logo.svg" alt="logo">
      <img src="@/assets/burger.svg" alt="menu toggle">
    </div>
    <HereMap
      apikey="mHGB5lfa-l_eUwb1gk-iL_hLhW8WQghNv5kOlOSLBNc"
      lat="52.51"
      lng="13.4"
      width="100%"
      height="100vh"
      :dataPoints="dataPoints"
    />
  </div>
</template>

<script>
/* eslint-disable no-undef */
import HereMap from '@/components/HereMap.vue'

export default {
  name: 'App',
  components: {
    HereMap
  },
  data () {
    return {
      dataPoints: []
    }
  },
  mounted () {
    this.dataPoints.push(new H.clustering.DataPoint(51.01, 0.01))
    this.dataPoints.push(new H.clustering.DataPoint(50.04, 1.01))
    this.dataPoints.push(new H.clustering.DataPoint(51.45, 1.01))
    this.dataPoints.push(new H.clustering.DataPoint(51.01, 2.01))
  }
}
</script>

<style lang="scss">
@import '@/assets/styles/main.scss';

.navbar {
  padding: 20px;
}
</style>
