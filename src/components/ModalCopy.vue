<template>
    <!-- New boxColor -->
    <div class="modalCopy" :style="modalStyles">
      <div class="modalCopy__content animated bounceIn">
        <h2>¡Copiado!</h2>
      </div>
    </div>
    <!-- END boxColor -->
</template>

<script>
export default {
  name: 'ModalCopy',
  props: {
    color: String,
  },
  computed: {
    modalStyles(){
      return{
        "background-color": this.color,
      }
    }
  },
  methods:{
    name : function(){

    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS cardColorto this component only -->
<style scoped lang="scss">
@import '../sass/main';
@import '../sass/components/modalCopy';
</style>
