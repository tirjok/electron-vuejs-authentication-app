<template>
    <div class="col-sm-6 col-sm-offset-3">
      <h1>Get a Free Chuck Norris Quote!</h1>
      <button class="btn btn-primary" @click="getQuote()">Get a Quote</button>
      <div class="quote-area" v-if="quote">
        <h2><blockquote>{{ quote }}</blockquote></h2>      
      </div>
    </div>
</template>


<script>
export default {
	data() {
		return {
			quote: ''
		}
	},

	methods: {
		getQuote() {
			this.quote = 'this is test'
		}
	}
}
</script>