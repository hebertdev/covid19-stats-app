<template>
 <div >
   <div class="card">
     <p class="card-header-title"> {{item.Country}} </p>
     <div class="legend-card">
       <ul>
         <li class="list-points"><span class="span-color-uno">. </span> Confirmados:  <span class="spandata">{{item.TotalConfirmed}}</span></li>
         <li class="list-points"><span class="span-color-cuatro">. </span> New confirmed: <span class="spandata">{{item.NewConfirmed}}</span></li>
         <br>
         <li class="list-points"><span class="span-color-dos">. </span> Recuperados:  <span class="spandata">{{item.TotalRecovered}}</span></li>
         <li class="list-points"><span class="span-color-cinco">. </span> New Recovered:  <span class="spandata">{{item.NewRecovered}}</span></li>
         <br>
         <li class="list-points"><span class="span-color-tres">. </span> Muertos: <span class="spandata">{{item.TotalDeaths}}</span></li>
         <li class="list-points"><span class="span-color-seis">. </span> New Deaths: <span class="spandata">{{item.NewDeaths}}</span></li>
         
       </ul>
       <nuxt-link :to="`/countries/${item.Slug}`" class="button-stats-country2"> Estadísticas </nuxt-link> 
     </div>
   </div>
 </div>
</template>
<script>
export default {
 props: {
   item: {
     type: Object
   }
 },
}
</script>
<style>

.card{
  background: white;
  margin: 10px 0;
  box-shadow: 0 2px 20px 0 rgba(0,0,0,0.22);
  padding: 10px;

}
.card-header-title{
  font-family: arial;
  font-weight: 600;
  color: #e83a57;
  color: #333333;
  text-align: center;
  display: block;
}

ul{
  padding: 0;
}

.list-points{
  list-style: none;
  display: flex;
  align-items: center;
}

.span-color-uno{
  display: block;
  width: 12px;
  height: 12px;
  display: flex;
  justify-content: center;
  align-items: center;
  background: #ffbc00;
  border-radius: 100%;
  color: #ffbc00;
  margin: 0 2px;
}

.span-color-dos{
  display: block;
  width: 12px;
  height: 12px;
  display: flex;
  justify-content: center;
  align-items: center;
  background: #33921b;
  border-radius: 100%;
  color: #33921b;
  margin: 0 2px;
}

.span-color-tres{
  display: block;
  width: 12px;
  height: 12px;
  display: flex;
  justify-content: center;
  align-items: center;
  background: #e83a57;
  border-radius: 100%;
  color: #e83a57;
  margin: 0 2px;
}

.span-color-cuatro{
  display: block;
  width: 12px;
  height: 12px;
  display: flex;
  justify-content: center;
  align-items: center;
  background: #b98901;
  border-radius: 100%;
  color: #b98901;
  margin: 0 2px;
}

.span-color-cinco{
  display: block;
  width: 12px;
  height: 12px;
  display: flex;
  justify-content: center;
  align-items: center;
  background: #1b610a;
  border-radius: 100%;
  color: #1b610a;
  margin: 0 2px;
}




.span-color-seis{  
  display: block;
  width: 12px;
  height: 12px;
  display: flex;
  justify-content: center;
  align-items: center;
  background: #a9132c;
  border-radius: 100%;
  color: #a9132c;
  margin: 0 2px;
}


.button-stats-country2{
 display: block;
 width: 100%;
 background: #e83a57;
 color: white;
 margin: 10px 0;
 text-decoration: none;
 display: flex;
 align-items: center;
 justify-content: center;
 font-family: arial;
 padding: 3px;
 border-radius: 5px; 
}

.spandata{
  display: block;
  margin: 0 5px;
}


</style>