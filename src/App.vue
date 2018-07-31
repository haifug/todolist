<template>
  <div id="app">
    <!--<img src="./assets/logo.png">-->
    <!--<router-view/>-->
    <v-todolist></v-todolist>
  </div>
</template>

<script>

	import todolist from "./components/Todolist.vue";
	
	export default {
	  name: 'App',
	  data(){
	  	return {
	  		
	  	}
	  },
	  components:{
	  	"v-todolist":todolist
	  }
	}
</script>

<style>

</style>
