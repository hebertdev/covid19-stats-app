
<template>
  <div class="card recipe-card">
    hola
  </div>
</template>
<script>
export default {
    props: ["country",]
};
</script>
<style>
.recipe-card {
    box-shadow: 0 1rem 1.5rem rgba(0,0,0,.6);
    height: 360px;
}

.container-img-profile{
  min-width: 130px;
  max-width: 130px;
  border-radius: 100%;
  min-height: 130px;
  max-height: 130px;
  overflow: hidden;
  display: flex;
  justify-content: center;
  align-items: center;
  margin:10px auto;
  border:1px solid rgba(0,0,0,0.19);


}

.container-img-profile img{
  width: 100%;
}


</style>