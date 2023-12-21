<template>
  <h1 class="hello">{{ msg }}</h1>
  <span class="hello__txt">{{ text }}</span>
  <button type="button" class="btn-click" @click="addNumber(1)">click number {{ addNumbers }}</button>
</template>

<script lang="ts">
  import { defineComponent } from 'vue';

  export default defineComponent({
    name: 'HelloWorld',
    data(){
      return{
        text:"하이하심미카!" as string,
        age:8 as number,
        addNumbers:1 as number
      }
    },
    props: {
      msg: String,
    },
    methods: {
      addNumber(num: number){
        if(this.addNumbers>=10) {
          this.addNumbers = 1;
        }else{
          this.addNumbers = this.addNumbers+num;
        }
      }
    },
    mounted(){
      console.log(this.text, this.age);
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
  .btn-click {
    margin:30px auto 0;
    width:150px;
    height:30px;
    display:block;
  }
</style>
