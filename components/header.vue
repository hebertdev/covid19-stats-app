<template>
  <div>
    <div class="header">
      <div class="max-header">

        <nuxt-link to="/" class="container-figure-logo"><img
         class="img-fluid"
         src="@/static/img/covid19.png"
         ></nuxt-link>

      </div>
    </div>
</div>
</template>


<script>
  export default{
    name:'headerone',
}

</script>

<style type="style" lang="css">
.header{
  width: 100%;
  height: 80px;
  background: white;
  position: fixed;
  z-index: 5;
  background: white;
  box-shadow: 0 2px 20px 0 rgba(0,0,0,0.22);
}

.max-header{
  max-width: 1000px;
  margin: auto;
  width: 95%;
  height: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.container-figure-logo{
  width: 80px;
  display: block;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}

.container-figure-logo img{
  width: 100%;
}

.btn-click{
  background: #782700;
  padding: 5px 10px;
  color: white;
  border-radius: 5px;
  cursor: pointer;
  color: white !important;
}

.modal-login{
  width: 100%;
  height: 100%;
  background: #0000008c;
  z-index: 10;
  display: flex;
  justify-content: center;
  align-items: center;
  position: fixed;

}

.modal-form-login{
  width: 400px;
  height: 280px;
  background: white;
  padding: 20px;
}

.title-login{
  font-family: arial;
  font-size: 30px;
  text-align: center;
  color: #333333;
}

.input-login-modal{
  display: block;
  width: 100%;
  box-sizing: border-box;
  border-radius: 5px;
  border:1px solid rgba(0,0,0,0.19);
  padding: 5px;

}

.button-login-form{
  background: orange;
  width: 100%;
  border:1px solid rgba(0,0,0,0.19);
  color: white;
  margin: 10px auto;
  padding: 5px;
  cursor: pointer;
  border-radius: 5px;
}


</style>
