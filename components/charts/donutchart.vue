<template>
	<div>
		<chartjs-doughnut/>
	</div>
</template>
<script>
	

	export default {
	 
	  props: ['data', 'options'],
	  mounted () {
	    this.renderChart(this.data, this.options)
	  }
	}
</script>