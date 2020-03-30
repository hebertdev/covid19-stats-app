<template>
  <div>

    <small class="txt-info-input">la primera letra en mayuscula </small>
    <input  class="inputSearchCountry" type="text" placeholder="buscar ejm: Peru" v-model="name" autocapitalize="word" >

    <div class="ListSearch">
      <li  v-for="item in searchUser" class="" v-model="name" v-if="name.length>0" >
        <nuxt-link v-if="item.TotalConfirmed>0" class="link-result" :to="`/countries/${item.Slug}`">{{ item.Country }}</nuxt-link>
      </li>

    </div>     

    <div class="let">

    </div>
    <small class="small-txt">Los datos provienen de <a href="https://github.com/CSSEGISandData/COVID-19" target="_blank" class="link-txt">Johns Hopkins CSSE.</a></small>
  </div>
</template>


<script>
  export default{
    name:'SearchCountry',
    data(){
      return{
        hola:'hola px',
        lists:[],
        name:'',

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
        return this.lists.filter((item) => item.Country.includes(this.name));
      }
    },

    created: function(){

      this.getUsers()

    }

  }

</script>

<style>

.txt-info-input{
  display: block;
  color: white;
  margin-bottom: -22px;
  padding: 5px;
}

.inputSearchCountry:first-letter {
  text-transform: uppercase;
}
.ListSearch{
  background: white;
  max-width: 500px;
  position: fixed;
  width: 90%;
  margin:auto;
  max-height: 300px;
  overflow: auto;
  border: 1px solid rgba(0,0,0,0.2)
  
}
.ListSearch li{
  list-style: none;
}

.link-result{
  font-family: arial;
  text-decoration: none;
  padding: 10px;
  color: #333333;
  display: block;
  background: ;
  margin-bottom: 5px;
  transition: all 0.2s;
}

.link-result:hover{
  background: rgba(0,0,0,0.3);
}
.inputSearchCountry{
  width: 100%;
  display: block;
  height: 35px;
  margin: 20px 0;
  border:none;
  border-radius: 15px;
  padding: 10px;
  color: #333333;
  font-size: 16px;
  border: 1px solid rgba(0,0,0,0.2)
}

.inputSearchCountry:first-letter {
  text-transform: uppercase;
}

.inputSearchCountry:focus{
  outline: none;
}

.small-txt{
  color: white;
}

.link-txt{
  color: white;
}

</style>
