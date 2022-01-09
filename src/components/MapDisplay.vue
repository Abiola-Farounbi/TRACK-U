<template>
<!-- The container to display the map -->
     <div id="mapContainer" class='w-full relative h-96 sm:h-60'></div>
</template>

<script>


export default {
  name: 'MapDisplay',
   props:{
    longitude:{
      type: Number,
      required: true,
      default:0
    },
    latitude:{
      type: Number,
      required: true,
      default:0
    },
   },
  mounted() { // lifecycle method to load the map 
    this.displayMap(); 
  },

  //  watch props for any change in value and the calls map function
  watch: {
    longitude() {
      this.displayMap();
    },
  
    latitude() {
      this.displayMap();
    },
  },
  methods: {
    displayMap(){
       // import the required JavaScript file for displaying the map
      let mapboxgl = require("mapbox-gl/dist/mapbox-gl.js");
       //access token
      mapboxgl.accessToken =  process.env.VUE_APP_MAP_TOKEN
      const map = new mapboxgl.Map({
      container: 'mapContainer', // container ID
      style: "mapbox://styles/mapbox/streets-v11",// style URL
      center: [this.longitude, this.latitude], // starting position [lng, lat]
      zoom: 5 // starting zoom    
      });
      //adding zoom and rotation controls
     map.addControl(new mapboxgl.NavigationControl());

     
    //  Create a default Marker, colored black.
    const marker = new mapboxgl.Marker({ color: 'black' })
    .setLngLat([this.longitude, this.latitude])
    marker.addTo(map);
  },
      
    }
}
</script>




