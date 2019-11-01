<template>
    <!-- New boxColor -->
    <a class="cardColor animated fadeIn" :id="`indexCard_${id}`">
      <div class="cardColor_color" :style="boxStyles" v-on:click="selectColor(color)">
        <div class="cardColor_content">
          <p class="cardColor_content_txt cardColor_content_txt--year">
            {{year}}
          </p>
          <div class="cardColor_content_txt cardColor_content_txt--center">
            <p>
              {{name}}
            </p>
            <p>
              {{color}}
            </p>
          </div>
          <p class="cardColor_content_txt cardColor_content_txt--pantone">
            {{pantone_value}}
          </p>
          <div class="cardColor_content_copy">
            <font-awesome-icon icon="eye-dropper" />
          </div>
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
    selectColor : function(color){
      // Wait to input value change
      let addColorToInput = () =>{
        return new Promise( (resolve)=>{
          this.$parent.clipBoard = color
          resolve()
        } )
      }
      // After value change
      addColorToInput().then( () =>{
        const inputToCopy = document.getElementById('clipBoard')
        inputToCopy.select()
        document.execCommand("copy")
      })

      // Open Modal
      this.$parent.openModal = true
      setTimeout(() => {
        this.$parent.openModal = false
      }, 1000);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS cardColorto this component only -->
<style scoped lang="scss">
@import '../sass/main';
@import '../sass/components/cardColor';
</style>
