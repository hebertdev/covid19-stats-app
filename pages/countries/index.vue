<template>
  <div class="">
   <headerone />
   <div style="height: 80px;background: red;"></div>
   <div class="max-container-title">
     <h1 style="" class="title-date">Datos hasta la fecha : {{date}} </h1> 
   </div>
   <div  class="container-all-countries">
     <countriesCard v-for="country in countries" :key="country.id" :country="country" v-if="country.TotalConfirmed>0" />

     </div>

   </div>
 </template>




 <script>
  import headerone from '~/components/header.vue'
  import countriesCard from '~/components/countries/countriesCard'

  export default {
    head() {
      return {
        title: "Lista de países"
      };
    },
    components: {
      countriesCard,
      headerone,
    },


    data: function() {
      return {
       rutanew: this.$route.path,
     };
   },





   asyncData ({ $axios }) {
    return $axios.get('/summary').then((res) => {




      var fecha =  new Intl.DateTimeFormat('es-PE' , {month:'long' , day:'numeric' , year:'numeric'}).format(new Date(res.data.Date))

      return {
        'countries':res.data.Countries ,
        'date':fecha,


      }
    })
  },

};


</script>


<style>

.container-all-countries{
  max-width: 1000px;
  width: 95%;
  margin:auto;
  display: grid;
  grid-template-columns: repeat(4, minmax(239px, 239px));
  grid-gap: 15px;
}

.title-date{
  text-align: center;
  font-size: 30px;
}

.max-container-title{
  max-width: 1000px;
  margin:auto;
}

.inputSearchCountries{
  width: 250px;
  display: block;
}

@media screen and (max-width: 600px){
  .container-all-countries{
    width: 95%;
    margin:auto;
    display: grid;
    grid-template-columns: repeat(1, minmax(300px, 550px));
    grid-gap: 15px;
  }
  .title-date{
    font-size: 20px;
    display: block;
    width: 95%;
    margin:auto;
    padding: 10px;
  }
}


</style>
