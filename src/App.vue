<template>
  <div id='app' class='font-serif m-0 p-0'>
   <div class="bg-primary h-1/2 py-8 px-8 ">
      <header>
        <h1 class='text-center my-4 text-white font-black text-2xl sm:text-xl '> 
           TRACK-U 
        </h1>
        <p class='text-center my-4 text-white font-black text-xl sm:text-base'> Highly Optimized IP Address Tracker </p>
      </header>
      <!-- The separate components -->
      <search-bar @trackIp="trackIpCall"/>
      <dashboard  :ipAddress="ipAddress" :isp="isp" :country="country" :countryFlag="countryFlag" :city="city" :currency="currency" :timezone="timezone" />
   </div>
    <map-display  :longitude="longitude" :latitude="latitude"/>
  </div>
</template>

<script> 
import axios from "axios";
import MapDisplay from './components/MapDisplay.vue'
import Dashboard from './components/Dashboard.vue'
import SearchBar from './components/SearchBar.vue'

export default {
  name: 'App',
  components: {
    MapDisplay,
    Dashboard,
    SearchBar
  },
   data() {
    return {
      searchInput: "",
      ipAddress: "",
      isp: "",
      longitude:0,
      latitude:0,
      country:"",
      countryFlag:"",
      city:"",
      currency:"",
      timezone:"",
      result:{}
    };
  },
    mounted: function () {
    this.getInfo();
  },
  methods:{
    // Function to get the value searched for
     trackIpCall(payload) {
      this.searchInput = payload;
      this.getInfo();
    },
  
  getInfo(){
    // The Api request
      const endpoint = `https://ipwhois.app/json/${this.searchInput}`
      axios.get(endpoint)
       .then((data) => data.data)
       .then((result) => {
        // Storing the values gotten
            this.ipAddress = result.ip
            this.isp = result.isp
            this.longitude = result.longitude
            this.latitude = result.latitude
            this.country = result.country
            this.countryFlag = result.country_flag
            this.city = result.city
            this.currency = result.currency
            this.timezone = result.timezone_gmt
            
          })
         
          .catch(error => {
            console.log(error.message)
          })
    },
 
  }
}
</script>



