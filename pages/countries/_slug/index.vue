<template>

  <div>
    <headerone />
    <div style="height: 90px"></div>
    <div class="container-detail-country">
      <div class="side-left-profile-country">
        <div class="container-profile-name-country">
          <figure class="figure-title-country">
            <h1 style="color: #333333;"> {{recuperados.Country}} </h1>
          </figure>
          <small class="txt-data-country">datos hasta la fecha: {{fecha}}</small>
          <div>
            <ul class="container-info-micro-data">
             <li class="list-points"><span class="span-color-uno">. </span> Confirmados: {{confirmados.Cases}} </li>
             <li class="list-points"><span class="span-color-dos">.</span> Recuperados: {{recuperados.Cases}} </li>
             <li class="list-points"><span class="span-color-tres">. </span> Muertos: {{muertos.Cases}} </li>
           </ul>
         </div>
         
       </div>
     </div>

     <div class="side-right-profile-country">
      <h1 class="txt-title-data-graphic" style="color: #333333;text-align: center;" > DATOS GENERALES </h1>
      <template>
        <ChartDoughnut />
      </template>
      <h1 class="txt-title-data-graphic" style="color: #333333;text-align: center;" > DATOS DESDE EL PRIMER CONFIRMADO </h1>
      <div>
        <template>
          <ChartBar v-if="loaded"/>
        </template>
        <a class="link-boton-regresar" href="javascript:window.history.back();">« Volver atrás</a>
        
      </div>
    </div>
  </div>

</div>

</template>
<script>


  import headerone from '~/components/header.vue';
  import ChartDoughnut from "@/components/charts/donutdetail";
  
  import ChartBar from "@/components/chart-bar";

  import axios from 'axios';

  import {route} from 'vue-router'
  


  export default {
    head() {
      return {
        title: "view Country"
      };
    },
    
    components:{
      headerone,
      ChartDoughnut,
      ChartBar,
    },

    data() {
      return {
        unarutadefinia : this.$route.path,
        recuperados : '',
        confirmados : '',
        muertos : '',
        fecha:'',
        loaded:false,
      };
    },

    methods: {
      async getUrl(){
        try {

          this.ruta3 = this.$route.path
          let paths = this.ruta3.split('/');
          let countridata = paths[paths.length-1];
          console.log(countridata)





          let countryrecovered = await this.$axios.$get(`/country/${countridata}/status/recovered/live`);
          let countryconfirmed = await this.$axios.$get(`/country/${countridata}/status/confirmed/live`);
          let countrydeaths = await this.$axios.$get(`/country/${countridata}/status/deaths/live`);



          let ultimorecoveredDato = countryrecovered[countryrecovered.length-1]
          let ultimoconfirmedDato = countryconfirmed[countryconfirmed.length-1]
          let ultimodeathsDato = countrydeaths[countrydeaths.length-1]

          let fechaformateada = new Intl.DateTimeFormat('es-PE' , {month:'long' , day:'numeric' , year:'numeric'}).format(new Date(ultimorecoveredDato.Date))
          this.fecha = fechaformateada;

          this.recuperados = ultimorecoveredDato
          this.confirmados = ultimoconfirmedDato
          this.muertos = ultimodeathsDato

          this.loaded = true



        } catch (e) {
          console.log(e)


        }
      }

    },

    mounted: function(){
      this.getUrl()
    },






  };
</script>
<style>
.link-boton-regresar{
  display: block;
  width: 290px;
  background: #e83a57;
  text-align: center;
  padding: 5px 10px;
  color: white;
  margin: 30px auto;
  text-decoration: none;
  font-family: arial;
  font-size: 14px;

}
.container-detail-country{
  max-width: 1000px;
  margin: auto;
  width: 100%;
  height: 100px;
  display: flex;
}

.side-left-profile-country{
  min-width: 200px;
  min-height: 200px;
}

.container-profile-name-country{
  width: 200px;
  height: 200px;

  position: fixed;
}

.figure-title-country{
  width: 100%;
  height: 100px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.list-points{
  list-style: none;
  display: flex;
  align-items: center;
}

.span-color-uno{
  display: block;
  width: 12px;
  height: 12px;
  display: flex;
  justify-content: center;
  align-items: center;
  background: #ffbc00;
  border-radius: 100%;
  color: #ffbc00;
  margin: 0 5px;
  
}

.span-color-dos{
  display: block;
  width: 12px;
  height: 12px;
  display: flex;
  justify-content: center;
  align-items: center;
  background: #33921b;
  border-radius: 100%;
  color: #33921b;
  margin: 0 5px;
}

.span-color-tres{
  display: block;
  width: 12px;
  height: 12px;
  display: flex;
  justify-content: center;
  align-items: center;
  background: #e83a57;
  border-radius: 100%;
  color: #e83a57;
  margin: 0 5px;
  
}

.button-stats-country{
 display: block;
 width: 100%;
 background: orange;
 color: white;
 margin: 10px 0;
 text-decoration: none;
 display: flex;
 align-items: center;
 justify-content: center;
 font-family: arial;
 padding: 3px;
 border-radius: 5px; 
}

.side-right-profile-country{
  width: 100%;
  height: 500px;
}

@media screen and (max-width: 600px){
  .container-detail-country{
    display: block;
  }

  .container-profile-name-country{
    width: 95%;
    height: 200px;
    margin:auto;

    position: relative;
  }
  .txt-data-country{
    display: block;
    width: 95%;
    margin:auto;
    text-align: center;
    font-size: 15px;
  }
  .container-info-micro-data{
    width: 95%;
    margin:20px auto;
  }
  .side-right-profile-country{
    width: 100%;
    height: auto;
    margin-top: 20px;
  }

  .txt-title-data-graphic{
    font-size: 20px;
    display: block;
    margin-top: 20px;
  }
}


</style>