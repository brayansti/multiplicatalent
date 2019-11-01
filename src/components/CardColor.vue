<template>
    <!-- New boxColor -->
    <a class="cardColor animated fadeIn" :id="`indexCard_${id}`">
      <div class="cardColor_color" :style="boxStyles" v-on:click="selectColor(color)">
        <div class="cardColor_content">
          <div>
            <p>
              {{name}}
            </p>
            <p>
              {{color}}
            </p>
          </div>
          <p>
            {{pantone_value}}
          </p>
          <p>
            {{year}}
          </p>
        </div>
      </div>
    </a>
    <!-- END boxColor -->
</template>

<script>
export default {
  name: 'CardColor',
  props: {
    color: String,
    id: Number,
    name: String,
    pantone_value: String,
    year: Number,
  },
  computed: {
    boxStyles(){
      return{
        "background-color": this.color,
      }
    }
  },
  methods:{
    selectColor : (color) =>{
      alert(color);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS cardColorto this component only -->
<style scoped lang="scss">
@import '../sass/main';
@import '../sass/components/cardColor';
@import '../sass/libraries/animateCSS';
</style>
