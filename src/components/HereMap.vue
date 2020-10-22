<template>
  <div ref="map" v-bind:style="{ width: width, height: height }"></div>
</template>

<script>
/* eslint-disable no-undef */

export default {
  name: 'HereMap',
  props: {
    apikey: String,
    lat: String,
    lng: String,
    width: String,
    height: String,
    dataPoints: Array
  },
  data () {
    return {
      map: {},
      platform: {}
    }
  },
  created () {
    this.platform = new H.service.Platform({
      apikey: this.apikey
    })
  },
  mounted () {
    // const clusteredDataProvider = new H.clustering.Provider(this.dataPoints)

    // // Create a layer that includes the data provider and its data points:
    // const layer = new H.map.layer.ObjectLayer(clusteredDataProvider)

    // // Add the layer to the map:
    // this.map.addLayer(layer)
    // Define a variable holding SVG mark-up that defines an icon image:
    const img = new Image()
    img.src = require('@/assets/home-default.svg')
    const imgIcon = img

    this.map = new H.Map(
      this.$refs.map,
      this.platform.createDefaultLayers().vector.normal.map,
      {
        zoom: 10
      }
    )

    // Create an icon, an object holding the latitude and longitude, and a marker:
    const icon = new H.map.Icon(imgIcon)
    const coords = { lng: this.lng, lat: this.lat }
    const marker = new H.map.Marker(coords, { icon: icon })

    // Add the marker to the map and center the map at the location of the marker:
    this.map.addObject(marker)
    this.map.setCenter(coords)
  }
}
</script>

<style scoped lang="scss">

</style>
