<template>
    <div class=" dashboard container mx-auto px-4 grid grid-cols-3 gap-x-16 gap-y-4 sm:block">
      <!-- div to show the IP address -->
        <div class='boardStyle'> 
            IP ADDRESS
            <p class='textStyle'> {{ipAddress}} </p>
        </div>

      <!-- div to show the Country -->
        <div class='boardStyle'>
            Country
            <p class='textStyle'> 
                {{country}}
                <img class='w-fit m-auto w-8' :src=countryFlag alt='Country Flag'/>
            </p>
        </div>
      <!-- div to show the City -->
        <div class='boardStyle'>
            City
            <p class='textStyle'> {{city}}</p>
        </div>
      <!-- div to show the ISP -->
        <div class='boardStyle'>
            isp
            <p class='textStyle'> {{isp}}</p>
        </div>
      <!-- div to show the Currency -->
        <div class='boardStyle'>
            currency
            <p class='textStyle'> {{currency}}</p>
        </div>
      <!-- div to show the timezone -->
        <div class='boardStyle'>
            timezone
            <p class='textStyle'> {{timezone}}</p>
        </div>
    </div>
</template>


<script>
export default {
  name: 'Dashboard',
  // Passing the values as props.
props: { 
    //the IP address fed in
      ipAddress:{
          type:String,
          required:true,
          default:''
      },
    //the ISP the user is using
     isp:{
          type:String,
          required:true,
          default:''
     },
     //the country where the device/use is currently located
   country:{
       type:String,
       required:true,
       default:''
   },
   //the image URL of the country flag
    countryFlag:{
         type:String,
         required:true,
          default:''
    },
    //the city where the device/use is currently located
    city:{
         type:String,
         required:true,
          default:''   
    },
    ////the currency of the country where the device/use is currently located
     currency:{
           type:String,
         required:true,
          default:''   
     },
     //the timezone where the device/use is currently located
    timezone:{
        type:String,
        required:true,
          default:''  
    }
}
}
</script>

<style scoped>

.dashboard div{
    background: rgba( 255, 255, 255, 0.2 );
    box-shadow: 0 8px 32px 0 rgba( 31, 38, 135, 0.37 );
    backdrop-filter: blur( 3.5px );
    -webkit-backdrop-filter: blur( 3.5px );
}

</style>
