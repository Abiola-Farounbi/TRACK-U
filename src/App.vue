<template>
  <div id='app'>
   <div class="bg-primary h-1/2 py-8 px-8 ">
      <header>
        <h1 class='text-center my-4 text-white font-black text-2xl sm:text-xl '> 
           TRACK-U 
        </h1>
        <p class='text-center my-4 text-white font-black text-xl sm:text-base'> Highly Optimized IP Address Tracker </p>
      </header>
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
      longitude:"",
      latitude:"",
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
     trackIpCall(payload) {
      this.searchInput = payload;
      this.getInfo();
    },
  
  getInfo(){
      const endpoint = `https://ipwhois.app/json/${this.searchInput}`
      axios.get(endpoint)
       .then((data) => data.data)
       .then((result) => {
        
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

<style scoped>

@import url('https://fonts.googleapis.com/css2?family=Roboto&display=swap');

#app {
  margin:0px;
  padding:0px;
  font-family: 'Roboto', sans-serif;
}
</style>>


