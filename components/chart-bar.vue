<template>
  <div class="card">
    

    <div class="card-img-bottom">
     
      
      <chartjs-bar
        v-for="(item, index) in types"
        :key="index"
        :backgroundcolor="item.bgColor"
        :beginzero="beginZero"
        :bind="true"
        :bordercolor="item.borderColor"
        :data="item.data"
        :datalabel="item.dataLabel"
        :labels="labels"
     
      
      />
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      beginZero: true,
      labels: [],
      types: [
        {
          bgColor: "#ffbc00",
          borderColor: "#ffbc00",
          data: [1, 3, 5, 7, 2, 4, 6],
          dataLabel: "Confirmados"
        },
        {
          bgColor: "#33921b",
          borderColor: "#33921b",
          data: [1, 5, 2, 6, 3, 7, 4],
          dataLabel: "Recuperados"
        },
        {
          bgColor: "#e83a57",
          borderColor: "#e83a57",
          data: [1, 3, 5, 7, 2, 4, 6],
          dataLabel: "Muertos"
        },
      ]
    };
  },
  methods: {
      async getUrl(){
        try {

        this.ruta3 = this.$route.path
        let paths = this.ruta3.split('/');
        let countridata = paths[paths.length-1];
        console.log(countridata)
        


       
        let countrydataall = await this.$axios.$get(`/total/dayone/country/${countridata}/status/confirmed`)
        let countrydataallre = await this.$axios.$get(`/total/dayone/country/${countridata}/status/recovered`)
        let countrydataallde = await this.$axios.$get(`/total/dayone/country/${countridata}/status/deaths`)
        


        var datafechasconfirmed = countrydataall.map(item=>new Intl.DateTimeFormat('es-PE' , {month:'long' , day:'numeric'}).format(new Date(item.Date)))
      
        var datacasosconfirmed = countrydataall.map(item=>item.Cases)
        var datacasosrecovered = countrydataallre.map(item=>item.Cases)
        var datacasosdeaths = countrydataallde.map(item=>item.Cases)





      

        this.labels = datafechasconfirmed
        
        this.types[0].data = datacasosconfirmed
        this.types[1].data = datacasosrecovered
        this.types[2].data = datacasosdeaths
        
      


        
        this.casos = countrydataall
        
      } catch (e) {
        console.log(e)
        

      }
      }
  
    },

    mounted: function(){
      this.getUrl()
    }
};
</script>