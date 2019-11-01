<template>
  <div id="app" v-if="posts">
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

    <article class="paginator">
      <div class="paginator__content">
        <a :class="currentPage == 1 ? '' : 'active'" class="paginator__arrow paginator__arrow-prev" v-on:click="prevPage()">
          Anterior
        </a>
        <a :class="currentPage == posts.total_pages ? '' : 'active'" class="paginator__arrow paginator__arrow-next" v-on:click="nextPage()">
          Siguente
        </a>
      </div>
    </article>
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
      currentPage: 1,
    }
  },
  methods: {
    getPosts () {
      const parameters = {
        url: 'https://reqres.in/api/colors',
        per_page: 9
      };
      console.time('consulta')
      axios.get(`${parameters.url}?page=${this.currentPage}&per_page=${parameters.per_page}`)
        .then(response => {
          this.posts = response.data
        })
        .catch(response => {
          this.error = response
        });
        console.timeEnd('consulta')
    },
    prevPage () {
      this.currentPage--
    },
    nextPage () {
      this.currentPage++
    },
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
  .paginator{
    padding: 20px;
    &__content{
      display: flex;
      justify-content: space-between;
    }
    &__arrow{
      padding: 15px;
      display: block;
      background-color: #efefef;
      border: 1px solid #ccc;
      user-select: none;
      pointer-events: none;
      opacity: 0.5;
      &.active{
        opacity: 1;
        pointer-events: all;
      }
      &-prev{}
      &-next{}
    }
  }
</style>
