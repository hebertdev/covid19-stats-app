<template>
  <div class="container">
   <headerone />
   
   <div class="banner">
    <div style="height: 80px"></div>
    <div>
      <globalData/>
    </div>
     <div class="max-banner">

       <div class="side-left">
         <h1 class="title-banner">Datos acerca del Covid-19</h1>
         <SearchCountry />
         <nuxt-link to="./countries" class="btn-view-all-countries">Ver todos los países</nuxt-link>
       </div>
       <div class="side-right">
                  <img
         style="width: 100%;"
         src="@/static/img/protegetedelcovid.png">
                  <div class="txt-description-author">SPA - PWA construido por <a href="https://www.instagram.com/hebertdev_/" target="_blank">Hebert Villafuerte</a> - 2020 </div>
       </div>
     </div>
   </div>

 </div>
</template>

<script>
  import Logo from '~/components/Logo.vue'
  import headerone from '~/components/header.vue'
  import SearchCountry from '~/components/includes/SearchCountry.vue'
  import globalData from '~/components/includes/globalData.vue'
  import ChartDoughnut from "@/components/chart-doughnut";


  export default {
    components: {
      Logo,
      headerone,
      SearchCountry,
      ChartDoughnut,
      globalData,

    }



  }
</script>

<style>

.txt-description-author{
  text-align: center;
  width: 100%;
  color: #666;
  margin:20px 0; 
}
.txt-description-author a{
  color: #666;
}
.banner{
  width: 100%;
  height: 100vh;
}
.max-banner{
  max-width: 1100px;
  display: flex;
  justify-content: center;
  align-items: center;
  margin: auto;
}

.title-banner{
  color: white;
  font-size: 60px;
  line-height: 60px;
  color: #333333;
}

.side-left{
  width: 47%;
  padding: 10px;
}

.side-right{
  width: 47%;
  padding: 10px;


}

.imgbanner{
  width: 100%;
}

.btn-view-all-countries{
  display: block;
  width: 200px;
  text-align: center;
  background: #e83a57;
  color: white;
  margin: 10px 0;
  padding: 10px;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 5px;
  font-family: arial;
  text-decoration: none;
}

.storbo{
  display: none;
}

@media screen and (max-width: 600px){
  .max-banner{
    display: block;
  }
  .title-banner{
    color: #333333;
    font-size: 40px;
    line-height: 40px;
  }

  .storbo{
    display: block;
    height: 80px;
  }
  .side-left{
    width: 95%;
    margin: auto;
  }

  .side-right{
    width: 95%;
    margin: auto;
  }
  .imgbanner{
    width: 60%;
    display: block;
    margin:auto;
  }

  .btn-view-all-countries{
    width: 100%;
  }

 

}

</style>
