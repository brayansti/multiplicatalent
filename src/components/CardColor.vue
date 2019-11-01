<template>
    <!-- New boxColor -->
    <a class="cardColor">
      <div class="cardColor_content" :style="boxStyles" v-on:click="selectColor(color)">
        <p>
          {{color}}
        </p>
        <p>
          {{id}}
        </p>
        <p>
          {{name}}
        </p>
        <p>
          {{pantone_value}}
        </p>
        <p>
          {{year}}
        </p>
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

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import '../sass/main';
@import '../sass/components/cardColor';
</style>
