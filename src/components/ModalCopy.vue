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
.modalCopy{
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 999;
  position: fixed;
  pointer-events: none;
  opacity: 0.9;
  display: flex;
  justify-content: center;
  align-items: center;
  &__content{
    color: $white;
    h2{
      @include fontSize(50);
    }
  }
}
</style>
