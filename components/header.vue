<template>
  <div>
    <div class="header">
      <div class="max-header">

        <nuxt-link to="/" class="container-figure-logo"><img
         class="img-fluid"
         src="@/static/img/covid19.png"
         ></nuxt-link>

         <div class="container-submenu-header">

           <div>
             <input onkeyup="javascript:this.value=this.value.toLowerCase();" type="text" placeholder="search Country" class="txt-search-input" v-model="country" autocomplete="off">
             <ul class="container-list-result-search" v-if="country.length>0">
               <li v-for="country in searchUser" class=""> <nuxt-link v-if="country.TotalConfirmed>0" class="result-continaer-item"  :to="`/countries/${country.Slug}`">{{country.Country}}</nuxt-link></li>

             </ul>
           </div>

           <ul class="ul-menu-header" v-bind:class="{'entrarysalir':enterandexit==true}">
             <div class="container-btn-menu-ul">
               <img class="icon-menuheader2" src="@/static/img/menu.png" alt="" v-on:click="enterandexit=false">
             </div>
             <li class="li-menu-header">
              <nuxt-link class="link-menu-header" v-bind:class="{'active':this.$route.path=='/quedateencasa'}"  to="/quedateencasa">Quédate en casa </nuxt-link>
            </li>
            <li class="li-menu-header">
              <nuxt-link class="link-menu-header" v-bind:class="{'active':this.$route.path=='/informacion'}"  to="/informacion">¿Qué es el Coronavirus? </nuxt-link>
            </li>
          </ul>

          <span class="btn-cross-roja" title="tienes síntomas?" v-on:click="modalemergency=true">+</span>
          <img v-on:click="enterandexit=true" class="icon-menuheader" src="@/static/img/menu.png" alt="">
        </div>

      </div>
    </div>
    <div class="modal-emergenci" v-if="modalemergency==true">
     <div class="container-sub-modal">
       <div class="header-modal"> <span>¿Tienes síntomas?</span> <span class="btn-close-modal" v-on:click="modalemergency=false">x</span> </div>
       <div style="padding: 10px;">
        <p>Puedes llamar a las lineas gratuitas del Gobierno - PERU</p>
        <br>
        <ul>
          <li>linea 1: <a class="link-free-call" href="tel:113"> 113 </a> </li>
          <li>linea 2: <a class="link-free-call" href="tel:952842623"> 952842623 </a> </li>
        </ul>
        <div style="display: flex;justify-content: space-between;align-items: center;width: 100%;">
          <a href="tel:113" class="link-one-emergency"> <img width="25" src="@/static/img/call.png" alt=""> Llamar ahora</a>
          <a href="https://api.whatsapp.com/send?phone=952842623&text=Hola%20necesito%20Ayuda" class="link-one-emergency"> <img width="25" src="@/static/img/whatsapp.webp" alt=""> Enviar Mensaje</a>
        </div>
        <p style="text-align: center;">Disponible las 24 horas</p>
        <br>
        <p>Escucha: Síntomas del Coronavirus</p>
        <iframe width="100%" height="100" scrolling="no" frameborder="no" allow="autoplay" src="https://w.soundcloud.com/player/?url=https%3A//api.soundcloud.com/tracks/774010129&color=%23ff5500&auto_play=false&hide_related=false&show_comments=true&show_user=true&show_reposts=false&show_teaser=true&visual=true"></iframe>
       </div>
     </div>

   </div>
 </div>
</template>

<script>
  export default{
    name:'headerone',
    
    data(){
      return{
        hola:'hola px',
        lists:[],
        country:'',
        rutaheader: this.$route.path,
        modalemergency:false,
        enterandexit:false,

      }
    },

    methods: {
      async getUsers(){
        try {


          let urlUsers = await this.$axios.$get(`/summary`)

          let nuevasurls = urlUsers.Countries
          this.lists = urlUsers.Countries
          console.log(this.lists)

        } catch (e) {
          console.log(e)

        }
      }

    },



    computed: {
      searchUser: function () {
        return this.lists.filter((item) => item.Slug.includes(this.country));
      }
    },

    created: function(){

      this.getUsers()

    }

  }

</script>


<style type="style" lang="css">
.modal-emergenci{
  position: fixed;
  width: 100%;
  height: 100vh;
  background: rgb(0,0,0,0.6);
  z-index: 10;
  display: flex;
  justify-content: center;
  align-items: center;
}

.link-one-emergency{
  display: block;
  width: 49%;
  
  color: white;
  padding: 5px;
  text-decoration: none;
  font-size: 14px;
  display: flex;
  align-items: center;
  justify-content: center;
  margin:10px 0;
  border-radius: 5px;
  border:1px solid #63c67d;
  color: #333333;

}

.link-one-emergency img{
  margin-right: 5px; 
}

.link-free-call{
  color: #333333;
}

.container-sub-modal{
  max-width:350px;
  width: 95%;
  margin:auto;
  background: white; 
  border-radius: 5px;
}

.header-modal{
  height: 40px;
  width: 100%;
  border-bottom: 1px solid rgba(0,0,0,0.2);
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;
}

.btn-close-modal{
  position: absolute;
  top: 0;
  right: 0;
  display: block;
  width: 30px;
  height: 30px;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 5px;
  background: #e83a57;
  font-family: arial;
  font-weight: 600;
  border-radius: 100%;
  margin:5px; 
  color: white;
  cursor: pointer;
}

.btn-close-modal:active{
  transform: scale(0.9);
}










.header{
  width: 100%;
  height: 50px;
  background: white;
  position: fixed;
  z-index: 5;
  background: white;
  border-bottom: 1px solid rgba(0,0,0,0.09)
}
.container-list-result-search{
  position: absolute;
  list-style: none;
  padding: 5px;background-color: white;
  border: 1px solid rgba(0,0,0,0.2);
  width: 250px;
  margin:5px 0;
}
.result-continaer-item{
  display: block;
  width: 100%;
  color: #665;
  padding: 2px;
  cursor: pointer;
  text-decoration: none;
}
.result-continaer-item:hover{
  background:rgba(0,0,0,0.1);
}
.txt-search-input{
  padding: 5px;
  display: block;
  border-radius: 5px;
  border: 1px solid rgba(0,0,0,0.15)
  
}

.txt-search-input:focus{
  outline: none;
}

.img-search-icon{
  width: 20px;
}

.max-header{
  max-width: 1000px;
  margin: auto;
  width: 95%;
  height: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.container-figure-logo{
  width: 35px;
  height: 35px;
  display: block;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 5px;
  overflow: hidden;
}

.container-figure-logo img{
  width: 110%;
}

.btn-click{
  background: #782700;
  padding: 5px 10px;
  color: white;
  border-radius: 5px;
  cursor: pointer;
  color: white !important;
}

.modal-login{
  width: 100%;
  height: 100%;
  background: #0000008c;
  z-index: 10;
  display: flex;
  justify-content: center;
  align-items: center;
  position: fixed;

}

.modal-form-login{
  width: 400px;
  height: 280px;
  background: white;
  padding: 20px;
}

.title-login{
  font-family: arial;
  font-size: 30px;
  text-align: center;
  color: #333333;
}

.input-login-modal{
  display: block;
  width: 100%;
  box-sizing: border-box;
  border-radius: 5px;
  border:1px solid rgba(0,0,0,0.19);
  padding: 5px;

}

.button-login-form{
  background: orange;
  width: 100%;
  border:1px solid rgba(0,0,0,0.19);
  color: white;
  margin: 10px auto;
  padding: 5px;
  cursor: pointer;
  border-radius: 5px;
}

.container-submenu-header{
  display: flex;
  align-items: center;
}

.ul-menu-header{
  display: flex;
  padding: 0;
}

.li-menu-header{
  list-style: none;
  margin-left: 20px;
}



.link-menu-header{
  padding:10px;
  font-family: arial;
  color: #333333;
  text-decoration: none;
  transition: all 0.3s;
  border-radius: 5px;
}

.link-menu-header:hover{
  color: white;
  background: #e83a57;
}

.active{
  background: #e83a57;
  color:white;
}

.btn-cross-roja{
  background: #e83a57;
  width: 35px;
  height: 35px;
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
  font-family: arial;
  font-weight: 600;
  border-radius: 5px;
  cursor: pointer;
  padding: 10px;
  margin-left: 10px;
  font-size: 25px;
}

.btn-cross-roja:active{
  transform: scale(0.9);
}

.icon-menuheader{
  width: 35px;
  margin-left: 10px; 
  cursor: pointer;
  padding: 2px;
  display: none;
}

.icon-menuheader2{
  width: 35px;
  margin-left: 10px; 
  cursor: pointer;
  padding: 2px;
  display: none;
}

.container-btn-menu-ul{

  display: none;

}
@media screen and (max-width: 600px){

  .icon-menuheader{
    display: block;
  }
  .ul-menu-header{
    display: block;
    position: absolute;
    width: 100%;
    height: 100vh;
    background: white;
    left:-660px;
    top: 0;
    transition: all 0.2s;
  }
  .entrarysalir{
    left: 0;
  }
  .li-menu-header{
    height: 50px;
    display: flex;
    justify-content: center;
    align-items: center;
    margin:20px auto; 
  }

  .container-btn-menu-ul{
    display: block;
    height: 40px;
  }

  .icon-menuheader2{
    display: block;
    margin:9px;
    float: right;
  }


}


</style>
