<template>
  <div class="card">
    

    
     
      
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
</template>

<script>
export default {
  data() {
    return {
      beginZero: true,
      labels: [],
      types: [
        {
          bgColor: "#0074D9",
          borderColor: "#0074D9",
          data: [1, 3, 5, 7, 2, 4, 6],
          dataLabel: "Tope"
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
  
        


       
        let countrydataall = await this.$axios.$get(`/total/dayone/country/${countridata}/status/confirmed`)
        
        


        var datafechasconfirmed = countrydataall.map(item=>new Intl.DateTimeFormat('es-PE' , {month:'long' , day:'numeric'}).format(new Date(item.Date)))
      
        var datacasosconfirmed = countrydataall.map(item=>item.Cases)
        var casesforday = datacasosconfirmed.reverse()
        casesforday.push(0)

     

        var resultado = [];
        for(var i = 0; i < casesforday.length-1;i++){
          resultado.push(casesforday[i]-casesforday[i+1]);
         

        }

        datacasosconfirmed = resultado.reverse()





        





  

        this.labels = datafechasconfirmed
        
        this.types[0].data = datacasosconfirmed
        
        
      

        
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