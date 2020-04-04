<template>
  <div class="container">
    <headerone />

    <div class="banner-information"  :style="{ backgroundImage:`url(${backgroundUrl})`}">


      <div class="max-banner-information">
        <div class="side-information-left">
          <h1 class="title-covid-banner-informationone">¿Qué es el coronavirus (covid19)  y como prevenirlo?</h1>
          <br class="br-title">
          <h1 class="title-covid-banner-informationtwo">#YoMeQuedoEnCasa</h1>
        </div>

      </div>



    </div>

    <div class="max-container-information">

      <div class="container-item-information">
        <div class="sub-container-item-information">
          <h2 class="title-txt-information">¿Qué es el Coronavirus?</h2>
          <span class="txt-description-information">
            Los coronavirus (CoV) son una amplia familia de virus que pueden causar diversas afecciones, desde el resfriado común, hasta infecciones respiratorias graves.

            Actualmente se investiga a un coronavirus surgido en la ciudad de Wuhan, China, al que se le ha denominado “Covid-19”.

            El 80% de los casos presentados en el mundo se presentan como una gripe normal y son fáciles de manejar, en tanto que el 20% puede hacer una complicación menor, de ellos un 10% necesita de hospitalización.
          </span>
        </div>
        <div class="sub-container-item-information">
         <img class="img-item-informacionxd" style="width: 100%;" src="@/static/img/coronavirus.png">
       </div>
     </div>

     <div class="container-item-information">
      <div class="sub-container-item-information">
        <img class="img-item-informacionxd" style="width: 100%;" src="@/static/img/china.png">
      </div>
      <div class="sub-container-item-information">
        <h2 class="title-txt-information" style="color: #de2910;">¿De dónde proviene?</h2>
        <span class="txt-description-information">
          Los primeros casos fueron reportados en la ciudad de Wuhan (China) que concentra más 90% de casos de esta enfermedad en el mundo. Actualmente se conocen casos en algunas zonas de Tailandia, Japón, Corea del Sur, Italia, España, Irak, Francia, Estados Unidos, México, Brasil, Ecuador, Chile, Perú, entre otros países.
        </span>

      </div>
    </div>

    <div class="container-item-information">
      <div class="sub-container-item-information">

       <h2 class="title-txt-information" style="color: black;">¿Cómo se transmite?</h2>
       <span class="txt-description-information">
        Se transmite de persona a persona a través de gotitas que expulsa una persona enferma al hablar, toser o estornudar.

        Las gotitas pueden ser inhaladas por las personas que están cerca al enfermo y también quedarse en cualquier tipo de superficie (pasamanos, mesas, lapiceros, entre otros) y ser tocadas por las manos.

        El virus ingresa a nuestro organismo cuando nos tocamos los ojos, la nariz y la boca con las manos sin lavar.
      </span>
    </div>
    <div class="sub-container-item-information">
      <img class="img-item-informacionxd" style="width: 100%;" src="@/static/img/trasmicion.png">

    </div>
  </div>

  <div class="container-item-information">
    <div class="sub-container-item-information">
      <img class="img-item-informacionxd" style="width: 100%;" src="@/static/img/ayudavirtual.png">

    </div>
    <div class="sub-container-item-information">

      <h2 class="title-txt-information" style="color: #e83a57;">Dónde comunicarse para recibir atención</h2>
      <span class="txt-description-information">
       Para mayor información, no dudes en llamarnos a la línea gratuita <a class="link-txt-description" href="tel:113">113</a> desde cualquier operador de telefonía fija o móvil, escribirnos al WhatsApp <a class="link-txt-description" href="tel:952842623">952842623</a> o al correo infosalud@minsa.gob.pe. Atendemos las 24 horas de los 365 días del año.
     </span>


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

.link-txt-description{
  color: #333333;
}


.banner-information{
  width: 100%;
  height: 100vh;
  background-repeat: no-repeat;
  background-size: cover;
  position: relative;
  background-position: center;

}

.banner-information::before{
  content: '';
  position: absolute;
  width: 100%;
  height: 100%;
  background:rgba(232, 58, 87, 0.73);
}
.max-banner-information{
  max-width: 1000px;
  width: 95%;
  margin: auto;
  height: 100%;
  background: ;
  position: absolute;
  left: 0;
  right: 0;
  display: flex;
  align-items: center;
  justify-content: space-between;

}

.side-information-left{
  width: 100%;
}

.title-covid-banner-informationone{
  color: white;
  font-size: 70px;
}

.title-covid-banner-informationtwo{
  color: white;
  font-size: 50px;
}
.max-container-information{
  max-width: 1000px;
  width: 95%;
  margin: auto;
}

.title-txt-information{
  font-size: 40px;
  color: #e83a57;
}



.container-item-information{
  width: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.sub-container-item-information{
  width: 45%;
  margin: 30px 0;
}
.txt-description-information{
  font-size: 23px;
  color: #333333;
}

.br-title{
  display: none;
}

@media screen and (max-width: 600px){
   .container-list-result-search{
    left: 0;
    width: 95%;
    right: 0;
    margin: 15px auto;
    max-height: 318px;
    overflow: hidden;
  }
  .br-title{
    display: block;
  }

  .result-continaer-item{
    display: block;
    width: 100%;
    color: #665;
    padding: 5px;
    cursor: pointer;
    text-decoration: none;
  }

  

  .container-item-information{
    display: block;
  }

  .sub-container-item-information{
    width: 100% !important;
  }
  .title-covid-banner-informationtwo{
    font-size: 30px !important;
    width: 100%;
    display: block;
  }
  .title-covid-banner-informationone{
    font-size: 40px !important;
  }
  .img-item-informacionxd{
    width: 70% !important;
    display: block;
    margin: auto;

  }
}
</style>
