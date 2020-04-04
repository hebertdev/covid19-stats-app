<template>
  <div class="container">
    <headerone />
    <div style="height: 60px;"></div>
    <div class="max-baner-quedatencasa">
      <img
      class="img-stop"
      style="width:200px;"
      src="@/static/img/stop.png">

      <h1 class="txt-title-quedaencasa">QUÉDATE EN CASA. SALVA VIDAS.</h1>
      <p style="text-align: center;">Ayuda a frenar el coronavirus</p>

      <div class="display-flex-item">

       <div class="item-quedatencasa">
         <h2 class="item-title-quedateencasa">Quédate en casa lo máximo posible</h2>
         <figure class="figure-item-quedaencasa">
           <img class="img-item-ss" 
           src="@/static/img/casa.png">
         </figure>
       </div>

       <div class="item-quedatencasa">
         <h2 class="item-title-quedateencasa">Mantén el distanciamiento social</h2>
         <figure class="figure-item-quedaencasa">
           <img  class="img-item-ss" 
           src="@/static/img/asilado.png">
         </figure>
       </div>

       <div class="item-quedatencasa">
         <h2 class="item-title-quedateencasa">Lávate las manos con frecuencia</h2>
         <figure class="figure-item-quedaencasa">
           <img  class="img-item-ss" 
           src="@/static/img/lavarse.png">
         </figure>
       </div>

       <div class="item-quedatencasa">
         <h2 class="item-title-quedateencasa">To se cubriéndote con el codo</h2>
         <figure class="figure-item-quedaencasa">
           <img  class="img-item-ss" 
           src="@/static/img/toser.png">
         </figure>
       </div>

       <div class="item-quedatencasa">
         <h2 class="item-title-quedateencasa">Llama si tienes síntomas</h2>
         <figure class="figure-item-quedaencasa">
           <img  class="img-item-ss" 
           src="@/static/img/llamar.png">
         </figure>
       </div>


     </div>
     <h1 style="text-align: center;color: #333333;padding: 10px;">SÍNTOMAS DEL CORONAVIRUS (COVID-19) - Escucha</h1>

     <iframe width="100%" height="400" scrolling="no" frameborder="no" allow="autoplay" src="https://w.soundcloud.com/player/?url=https%3A//api.soundcloud.com/tracks/774010129&color=%23ff5500&auto_play=false&hide_related=false&show_comments=true&show_user=true&show_reposts=false&show_teaser=true&visual=true"></iframe>
   </div>

   


 </div>
</template>

<script>
  import headerone from '~/components/header.vue'
  import backgroundUrl from '~/assets/banner.jpg'


  export default {
    components: {
      headerone,

    },
    data(){
      return{
        backgroundUrl
      }
    }



  }
</script>

<style>

.img-item-ss{
  width: 100px;
  display: block;
  margin: 20px auto;
}

.max-baner-quedatencasa{
  max-width: 1000px;
  width: 95%;
  margin: auto;


}
.item-title-quedateencasa{
  color: #333333;
  font-size: 18px;
  text-align: center;
}
.img-stop{
  display: block;
  margin:20px auto;
}

.txt-title-quedaencasa{
  font-size: 45px;
  color: #333333;
  text-align: center;
}

.item-quedatencasa{
  width: 300px;
  margin:30px;
}

.display-flex-item{
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}

@media screen and (max-width: 600px){
  .txt-title-quedaencasa{
    font-size: 25px;
    color: #333333;
    text-align: center;
  }
}

</style>
