<template>
    <div class=" dashboard container mx-auto px-4 grid grid-cols-3 gap-x-16 gap-y-4 sm:block">
        <div> 
            IP ADDRESS
            <p class='my-2 font-black text-xl'> {{ipAddress}} </p>
        </div>
        <div>
            County
            <p class='my-2 font-black text-xl text-center'> 
                {{country}}
                <img class='w-fit m-auto w-8' :src=countryFlag alt='Country Flag'/>
            </p>
        </div>
        <div>
            city
            <p class='my-2 font-black text-xl sm:text-base'> {{city}}</p>
        </div>
        <div>
            isp
            <p class='my-2 font-black text-xl sm:text-base'> {{isp}}</p>
        </div>
        <div>
            currency
            <p class='my-2 font-black text-xl sm:text-base'> {{currency}}</p>
        </div>
        <div>
            timezone
            <p class='my-2 font-black text-xl sm:text-base'> {{timezone}}</p>
        </div>
    </div>
</template>
<style scoped>
.dashboard div{
    height:100px;
    background: rgba( 255, 255, 255, 0.2 );
    box-shadow: 0 8px 32px 0 rgba( 31, 38, 135, 0.37 );
    backdrop-filter: blur( 3.5px );
    -webkit-backdrop-filter: blur( 3.5px );
    border-radius: 10px;
    color:white;
    text-align: center;
    font-size: 15px;
    padding:10px;
    text-transform: uppercase;
}

@media only screen and (min-width:100px) and (max-width:500px){
    .dashboard div{
    height:100px;
   margin:10px 0px;
   font-size: 12px;
}
}

</style>
<script>
export default {
  name: 'Dashboard',
  props: [ "ipAddress", "isp", "country", "countryFlag" , "city" , "currency" ,"timezone"],
}
</script>