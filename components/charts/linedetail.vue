<template>
  <div class="">
  
      


      <chartjs-line
        
        :backgroundcolor="bgColor"
        :beginzero="beginZero"
        :bind="true"
        :bordercolor="borderColor"
        :data="data[radio]"
        :datalabel="dataLabel"
        :labels="labels[radio]"
      />


      <li v-for="caso in casos" :key="caso.id">
       {{casos.Date}}
      </li>


      

  </div>
</template>

<script>
export default {
  data() {
    return {
      casos:'',
      bgColor: "red",
      beginZero: true,
      borderColor: "red",
      
      
      
      data: {
        day: [1, 8, 4,5,  4, 2],
        week: [12, 14, 16, 18, 11, 13, 15]
      },

      dataLabel: "Foo",
      labels: {
        day: [],
        week: ["Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat"]
      },
      radio: "day"
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
        
        var datanew = countrydataall.map(item=>item.Date)

        var datados = [1,2,3,4,5]
        
        console.log(countrydataall[5].Date)

        var fechasData = Object.values(this.labels);
        var newFechasData = fechasData[0]

        this.newFechasData = datanew


        console.log(newFechasData)
        console.log(datanew)


        

        

        
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