<template>
  <div id="translateform">
  
	<form class="form-inline" v-on:submit="submit">
		<input class="form-control" type="text" v-model='textToTranslate' placeholder="Enter a text to translate">
		<select  class="form-control" v-model="language">
			<option value="ar">Arabic</option>
			<option value="fr">French</option>
			<option value="en">English</option>
			<option value="ru">Russian</option>
		</select>
		<input class="btn btn-primary" type="submit" value="Translate">
	</form>
  
  </div>
</template>

<script>
export default {
  name: 'translateform',

  data () {
    return {
    	textToTranslate:'',
    	language:'ru'
    }
  },
  methods:{
  	submit(e){
  		e.preventDefault()
  		this.$emit('formSubmit', this.textToTranslate, this.language)
  	}
  }
}
</script>

<style>
.form-inline{
	display: flex;
}
input.form-control{
	flex: 1;
}

</style>
