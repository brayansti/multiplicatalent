<template>
    <!-- New boxColor -->
    <div class="boxColor" :style="boxStyles">
      <div class="colorsGrid__item_info">
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
    </div>
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
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.boxColor{
    width: calc(50% - 20px);
    margin: 10px 10px;
}
</style>
