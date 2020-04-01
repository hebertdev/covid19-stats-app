<template>
  <div>
    <div class="header">
      <div class="max-header">

        <nuxt-link to="/" class="container-figure-logo"><img
         class="img-fluid"
         src="@/static/img/covid19.png"
         ></nuxt-link>

         <div>
           <input onkeyup="javascript:this.value=this.value.toLowerCase();" type="text" placeholder="search Country" class="txt-search-input" v-model="country" autocomplete="off">
           <ul class="container-list-result-search" v-if="country.length>0">
             <li v-for="country in searchUser" class=""> <nuxt-link v-if="country.TotalConfirmed>0" class="result-continaer-item"  :to="`/countries/${country.Slug}`">{{country.Country}}</nuxt-link></li>
            
           </ul>
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
.header{
  width: 100%;
  height: 50px;
  background: white;
  position: fixed;
  z-index: 5;
  background: white;
  border-bottom: 1px solid rgba(0,0,0,0.05)
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
  border: 1px solid rgba(0,0,0,.3);
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

@media screen and (max-width: 600px){
  .container-list-result-search{
    left: 0;
    width: 95%;
    right: 0;
    margin: 15px auto;
    max-height: 318px;
    overflow: hidden;
  }

  .result-continaer-item{
    display: block;
    width: 100%;
    color: #665;
    padding: 5px;
    cursor: pointer;
    text-decoration: none;
  }
}


</style>
