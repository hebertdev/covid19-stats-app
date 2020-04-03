<template>
  <div>
   
      <h2 class="card-title-donut">Datos totales de Covid19 en el mundo a la fecha 31 de marzo 2020</h2>



    
      <chartjs-doughnut
        :bind="true"
        :datasets="datasets"
        :labels="labels"
        :option="option"
      />

  </div>
</template>


<script>
export default {
  data() {
    return {
      datacollection:null,
      loaded:false,
      recuperadosCases:'',
      datasets: [
        {
          data: [],
          backgroundColor: ["#ffdb3b", "#33921b", "#e83a57"],
          hoverBackgroundColor: ["#ffdb3b", "#33921b", "#e83a57"]
        }
      ],
      labels: ["Confirmados", "Recuperados", "Muertos"],
      option: {},
    };

  },

  methods: {
      async getUrl(){
        try {

      
        
        let alldata = await this.$axios.$get(`/all`);
        
  
        let ultimodato = alldata[alldata.length-1]
      

        console.log(ultimodato + 'hola')
 
        let newdata = this.datasets[0].data

         this.data = [this.confirmadosCases , this.confirmadosCases, this.muertosCases]
   
         this.recuperadosCases = ultimorecoveredDato.Cases
         this.loaded = true
        
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


<style>
  .card-title-donut{
    text-align: center;
    display: block;
    width: 100%;
    color: #333333;
  }
</style>