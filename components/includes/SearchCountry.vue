<template>
  <div>
    <form action="" >
      <input class="inputSearchCountry" type="text" placeholder="buscar ejm: Peru">
    </form>
    <small class="small-txt">Los datos provienen de <a href="https://github.com/CSSEGISandData/COVID-19" target="_blank" class="link-txt">Johns Hopkins CSSE.</a></small>
  </div>
</template>


<script>
  export default{
    name:'SearchCountry',
  }

</script>

<style>

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
