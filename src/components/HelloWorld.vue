<template>
  <h1 class="hello">{{ msg }}</h1>
  <span class="hello__txt">{{ text }}</span>
</template>

<script lang="ts">
  import { defineComponent } from 'vue';

  export default defineComponent({
    name: 'HelloWorld',
    data(){
      return{
        text:"하이하심미카!"
      }
    },
    props: {
      msg: String,
    },
    mounted(){
      let age = 8;
      console.log(this.text, age);      
    }
  });
</script>

<style lang="scss">
  h3 {
    margin: 40px 0 0;
  }
  .hello {
    &__txt {
      color:#000;
    }
  }
</style>
