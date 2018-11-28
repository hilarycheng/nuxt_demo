<template>
  <section class="section">
	<div class="container">
  	  <div class="rows">
            <button class="primary" v-on:click="goBack">Back</button>
	    <h1 class="title">Comments</h1>
    	    <div v-for="comment in comments" :key="comment.id" class="row is-one-quarter">
      	      <div class="columns">
        	<div class="column">
          	  <div class="card">
            	    <div class="card-header">
              	      <div class="card-header-title">
                	{{ comment.name }} {{ comment.email }}
              	      </div>
            	    </div>
            	    <div class="card-content">
              	      {{ comment.body }}
            	    </div>
          	  </div>
        	</div>
      	     </div>
    	   </div>
  	  </div>
	</div>
  </section>
</template>
<script>
export default {
	async asyncData({ app, params }) {
  	  const comments = await app.$axios.$get('https://jsonplaceholder.typicode.com/posts/' + params.id + '/comments');

  	  console.log('Loading Comments ' + params.id);

  	  return { comments };
	},
        methods: {
          	goBack: function(event) {
            	  event.stopPropagation()
            	  this.$router.go(-1);
          	}
        }
}
</script>
