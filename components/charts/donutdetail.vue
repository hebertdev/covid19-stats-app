<template>
  <div class="" style="margin-bottom: 30px;">

    <div class="" >
      <chartjs-doughnut v-if="loaded"
        :bind="true"
        :datasets="datasets"
        :labels="labels"
        :option="option"
      />
    </div>
   

 
  </div>

</template>

<script>
export default {
  data() {
    return {
      datacollection:null,
      loaded:false,
      hola:65,
      recuperadosCases:'',
      confirmadosCases:'',
      muertosCases:'',
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

        console.log(ultimoconfirmedDato.Cases)
        console.log(ultimorecoveredDato.Cases)
        console.log(ultimodeathsDato.Cases)

        let newdata = this.datasets[0].data

        newdata.push(ultimoconfirmedDato.Cases,ultimorecoveredDato.Cases,ultimodeathsDato.Cases)

        console.log(newdata)


         this.data = [this.confirmadosCases , this.confirmadosCases, this.muertosCases]
        
         this.confirmadosCases = ultimoconfirmedDato.Cases
         this.recuperadosCases = ultimorecoveredDato.Cases
         this.muertosCases = ultimodeathsDato.Cases

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