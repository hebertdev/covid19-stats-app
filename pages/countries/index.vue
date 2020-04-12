<template>
  <div class="">
   <headerone />
   <div style="height: 50px;background: red;"></div>
   <globalData/>

   <div class="max-container-title">
     <h1 style="" class="title-date">Datos hasta la fecha : {{date}} </h1> 
   </div>
   <div class="max-container-search">
     <div>

      <input onkeyup="javascript:this.value=this.value.toLowerCase();"   class="inputSearchCountry" type="text" placeholder="buscar ejm: Peru"  autocapitalize="word" v-model="namecountry" >    

      <div class="let">

      </div>
      <small class="small-txt">Los datos provienen de <a href="https://github.com/CSSEGISandData/COVID-19" target="_blank" class="link-txt">Johns Hopkins CSSE.</a></small>
    </div>
  </div>
  <div  class="container-all-countries">
   <countriesCard v-for="item in searchUser"  :item="item" :key="item.id" v-if="item.TotalConfirmed>0" />
  
   </div>

 </div>
</template>




<script>
  import headerone from '~/components/header.vue'
  import countriesCard from '~/components/countries/countriesCard'
  import SearchCountry from '~/components/includes/SearchCountry.vue'
  import globalData from '~/components/includes/globalData.vue'



  export default {
    head() {
      return {
        title: "Lista de países"
      };
    },
    components: {
      countriesCard,
      headerone,
      globalData,


    },


    data: function() {
      return {
       rutanew: this.$route.path,
       countrylist:[],
       namecountry:'',
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


  computed: {
      searchUser: function () {
        return this.countries.filter((item) => item.Slug.includes(this.namecountry));
      }
    },

};


</script>


<style>

.max-container-search{
  max-width: 1000px;
  margin: auto;
  width: 95%;
}
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
