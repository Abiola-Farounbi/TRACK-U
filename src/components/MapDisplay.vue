<template>
     <div id="map"></div>
</template>

<script>
import mapboxgl from "mapbox-gl";

export default {
  name: 'MapDisplay',
  props: ["longitude", "latitude"],
  mounted() { // lifecycle to load the map upon page load
    this.displayMap();
  },
  methods: {
    displayMap(){
      mapboxgl.accessToken =  process.env.VUE_APP_MAP_TOKEN
      const map = new mapboxgl.Map({
      container: 'map', // container ID
      style: "mapbox://styles/mapbox/streets-v11",// style URL
      center: [this.longitude, this.latitude], // starting position [lng, lat]
      zoom: 5 // starting zoom    
      });
     map.addControl(new mapboxgl.NavigationControl());

     
    //  Create a default Marker, colored black, rotated 45 degrees.
    const marker = new mapboxgl.Marker({ color: 'black' })
    .setLngLat([this.longitude, this.latitude])
    marker.addTo(map);
  },
    }
}
</script>



<style scoped>

#map {
  position: relative;
  z-index: 1;
  height: 60vh;
  width: 100%;
}
@media only screen and (min-width:100px) and (max-width:500px){
  #mapid { height: 40vh; }
}
</style>

