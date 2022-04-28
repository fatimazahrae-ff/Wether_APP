<!-- Please remove this file from your project -->
<template>
  <div
    class="relative flex items-top justify-center min-h-screen bg-pink-100 sm:items-center sm:pt-0"
  >
   
    <div class="max-w-4xl mx-auto sm:px-6 lg:px-8">
      <img
        class="flex justify-center w-48 "
        src="https://www.pngmart.com/files/3/Weather-PNG-HD.png"
     
      >
      <div class="mt-8 bg-white overflow-hidden shadow sm:rounded-lg p-6">
        <h2 class="text-2xl leading-7 font-semibold">
          Welcome to MY CITY WEATHER
        </h2>
        <p class="mt-3 text-gray-600">
          We recommend you enter your city name  to receive your Weather
        </p>
        <section class="flex justify-center mt-10">
          <input v-model="city" placeholder="Name"  class="p-5 m-8 border-2 transition duration-500 h-11 placeholder-purple-700 focus:placeholder-transparent border-purple-700 w-4/12 text-center text-purple-700 bg-transparent rounded-md focus:outline-none">
         <button  class="p-5 m-8 border-2  h-11  border-purple-700 w-4/12 text-center  text-white bg-purple-700 font-medium rounded-lg text-sm px-5 py-2.5 text-center mb-2 hover:bg-purple-800"  @click="getData()">
          Button
        </button>
        </section>

        <section>
         Name : {{ name}} <br>
         Country : {{ country}} 
        </section>
        <section>
         Temperature in celsius : {{ temperature}} C <br>
         description : {{ description}} 
        </section>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: 'NuxtTutorial',
 data() {
    return {
      Weather: {},
      temperature : null,
      city : null,
      name : null, 
      country : null , 
      description : null 
    }
},
  methods:{

    getData(){
      axios
        .get('https://api.weatherapi.com/v1/current.json?key=3fd6033c520e470b955110027222804&q='+this.city+'&aqi=yes')
        .then(response => {this.Weather = response.data;
        this.temperature = response.data.current.temp_c;
        this.name = response.data.location.name;
        this.country = response.data.location.country;
        this.description = response.data.current.condition.text;

        })
    }



      
      
      }   
    
  
   
}
</script>
