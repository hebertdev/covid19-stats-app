<template>
	<div>

		<h1 class="title-covid-global-data" style="text-align: center;color: #666;">DATOS TOTALES DEL COVID19 EN EL MUNDO</h1>
		<div class="container-global-data">
			<ul>
				<li class="list-li"> <span class="puntos-colors" style="background: #ffbc00;"></span> <span class="txt-info-ddata">Confirmados: {{dataGlobal.TotalConfirmed}}</span></li>
				<li class="list-li"> <span class="puntos-colors" style="background: #b98901;"></span> <span class="txt-info-ddata">Nuevos casos: {{dataGlobal.NewConfirmed}}</span></li>
			</ul>
			<ul>
				<li class="list-li"> <span class="puntos-colors" style="background: #33921b;"></span> <span class="txt-info-ddata">Recuperados: {{dataGlobal.TotalRecovered}}</span></li>
				<li class="list-li"> <span class="puntos-colors" style="background: #1b610a;"></span> <span class="txt-info-ddata">Nuevos Casos: {{dataGlobal.NewRecovered}}</span></li>
			</ul>
			<ul>
				<li class="list-li"> <span class="puntos-colors" style="background: #e83a57;"></span> <span class="txt-info-ddata">Muertos: {{dataGlobal.TotalDeaths}}</span></li>
				<li class="list-li"> <span class="puntos-colors" style="background: #a9132c;"></span> <span class="txt-info-ddata">Nuevos casos: {{dataGlobal.NewDeaths}}</span></li>
			</ul>
		</div>
	</div>
</template>


<script>
	export default{
		name:'globalData',
		data(){
			return{
				dataGlobal:'',

			}
		},

		methods: {
			async getUsers(){
				try {

					let urlUsers = await this.$axios.$get(`/summary`)
					let nuevasurls = urlUsers.Countries
					this.dataGlobal = urlUsers.Global
				} catch (e) {
					console.log(e)

				}
			}

		},

		created: function(){
			this.getUsers()
		}
	}
</script>



<style>

.title-covid-global-data{
	text-align: center;
	color: #666;
	display: block;
	max-width: 900px;
	width: 95%;
	margin: auto;
}

.container-global-data{
	max-width: 1000px;
	width: 95%;
	margin:20px auto;
	display: flex;
	justify-content: space-between; 

}

.list-li{
	list-style: none;
	display: flex;
	align-items: center;
	margin-bottom: 10px;
}

.puntos-colors{
	padding: 2px;
	border-radius: 100%;
	display: block;
	width: 15px;
	height: 15px;
	margin-right: 5px;
}
.txt-info-ddata{
	font-size: 20px;
	font-family: arial;
	color: #666;
} 
@media screen and (max-width: 600px){
	.container-global-data{
		display: block;
	}

	.title-covid-global-data{
		font-size: 30px;
	}
}
</style>
