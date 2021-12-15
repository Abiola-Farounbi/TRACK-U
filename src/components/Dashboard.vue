<template>
    <div class=" dashboard container mx-auto px-4 grid grid-cols-3 gap-x-16 gap-y-4 sm:block">
        <div class='boardStyle'> 
            IP ADDRESS
            <p class='textStyle'> {{ipAddress}} </p>
        </div>
        <div class='boardStyle'>
            County
            <p class='textStyle'> 
                {{country}}
                <img class='w-fit m-auto w-8' :src=countryFlag alt='Country Flag'/>
            </p>
        </div>
        <div class='boardStyle'>
            city
            <p class='textStyle'> {{city}}</p>
        </div>
        <div class='boardStyle'>
            isp
            <p class='textStyle'> {{isp}}</p>
        </div>
        <div class='boardStyle'>
            currency
            <p class='textStyle'> {{currency}}</p>
        </div>
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
      ipAddress:{
          type:String,
          required:true,
          default:''
      },
     isp:{
          type:String,
          required:true,
          default:''
     },
   country:{
       type:String,
       required:true,
       default:''
   },
    countryFlag:{
         type:String,
         required:true,
          default:''
    },
    city:{
         type:String,
         required:true,
          default:''   
    },
     currency:{
           type:String,
         required:true,
          default:''   
     },
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
