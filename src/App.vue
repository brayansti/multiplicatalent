<template>
  <div id="app">
    <article class="colorsGrid">
      <CardColor
        v-for="post in posts.data"
        v-bind:key="post.id"
        :color="post.color"
        :id="post.id"
        :name="post.name"
        :pantone_value="post.pantone_value"
        :year="post.year"
      />
    </article>
    <div>
        <input type="text" v-model="currentPage">
    </div>
  </div>
</template>

<script>
import CardColor from './components/CardColor.vue'
import axios from 'axios'

export default {
  name: 'app',
  data () {
    return{
      loading: false,
      posts: null,
      error: null,
      currentPage: 1
    }
  },
  methods: {
    getPosts () {
      axios.get('https://reqres.in/api/colors?page='+this.currentPage)
        .then(response => {
          this.posts = response.data;
        })
        .catch(response => {
          console.log(response);
        });
    }
  },
  created () {
    this.getPosts();
  },
  watch: {
    currentPage () {
      this.getPosts()
    }
  },
  components: {
    CardColor
  }
}
</script>

<!-- Global Styles -->
<style lang="scss">
  @import './sass/main';
  @import './sass/components/flexgrid';
</style>
