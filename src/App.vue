<template>
  <div id="app" v-if="posts">
    <input class="hidden" id="clipBoard" v-model="clipBoard" type="text">
    <header>
      <h1 class="taC pt15 pb15">
        Colores
      </h1>
    </header>
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
          <font-awesome-icon icon="chevron-left" />
          <span>Anterior</span>
        </a>
        <p> {{currentPage}} / {{posts.total_pages}}</p>
        <a :class="currentPage == posts.total_pages ? '' : 'active'" class="paginator__arrow paginator__arrow-next" v-on:click="nextPage()">
          <span>Siguente</span>
          <font-awesome-icon icon="chevron-right" />
        </a>
      </div>
    </article>
  </div>
</template>

<script>
import CardColor from './components/CardColor.vue'
import axios from 'axios'

// Icons
import { library } from '@fortawesome/fontawesome-svg-core'
import { faChevronRight , faChevronLeft, faEyeDropper } from '@fortawesome/free-solid-svg-icons'
library.add(faChevronRight , faChevronLeft, faEyeDropper)

export default {
  name: 'app',
  data () {
    return{
      loading: false,
      posts: null,
      error: null,
      currentPage: 1,
      clipBoard: '',
    }
  },
  methods: {
    // Method to call data
    getPosts () {
      // Tarameters to get Data
      const parameters = {
        url: 'https://reqres.in/api/colors',
        per_page: 9
      };
      axios.get(`${parameters.url}?page=${this.currentPage}&per_page=${parameters.per_page}`)
        .then(response => {
          this.posts = response.data
        })
        .catch(response => {
          this.error = response
        });
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
  @import './sass/components/paginator';
  header{
    color: $white;
    background: linear-gradient(90deg, rgba(131,58,180,1) 0%, rgba(253,29,29,1) 50%, rgba(252,176,69,1) 100%);
  }
</style>
