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
      datasets: [
        {
          data: [783.891, 159.228, 37.759 ],
          backgroundColor: ["orange", "#33921b", "#e83a57"],
          hoverBackgroundColor: ["orange", "#33921b", "#e83a57"]
        }
      ],
      labels: ["Confirmados", "Recuperados", "Fallecidos"],
      option: {}
    };
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