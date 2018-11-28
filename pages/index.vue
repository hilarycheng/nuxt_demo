<template>
  <section class="section">
      <div class="container">
  	<div class="rows">
    	  <h1 class="title">Posts</h1>
    	    <div class="columns is-multiline">
      	       <div v-for="post in posts" :key="post.id" class="column is-one-quarter">
                 <div class="card" v-on:click="postClick(post.id, $event)"> 
          	    <div class="card-header">
            	      <div class="card-header-title">
              	        {{ post.title }}
            	      </div>
          	    </div>
          	    <div class="card-content">
            	      {{ post.body }}
          	    </div>
        	  </div>
      	        </div>
    	      </div>
  	    </div>
	</div>
  </section>
</template>

<script>
import AppLogo from '~/components/AppLogo.vue'

export default {
  components: {
    AppLogo
  },
  async asyncData({ app }) {
	const posts = await app.$axios.$get('https://jsonplaceholder.typicode.com/posts');
	console.log('Loading Posts');
	return { posts };
  },
  methods: {
	postClick: function(postid, event) {
  	  event.stopPropagation();
  	  this.$router.push('/post/' + postid);
	}
  }
}
</script>

<style>
.container {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif; /* 1 */
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>

