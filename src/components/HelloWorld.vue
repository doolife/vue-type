<template>
  <h1 class="hello">{{ msg }}</h1>
  <span class="hello__txt">{{ text }}</span>
  <button type="button" class="btn-click" @click="addNumber(1)">click number {{ addNumbers }}</button>
  <button type="button" class="add-text">add text</button>
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
      },
      addText(evt: MouseEvent, name: string) {
        (evt.target as HTMLElement).innerText = name;
      },
      numOrStr(a: number | string) {
        // a.toFixed(1); // toFixed 메소드는 number 전용 메소드이기 때문에 타입 가드를 해주지않으면 에러
        // 타입 가드
        if (typeof a === 'number') {  // 아규먼트 a가 number or string 될 수 있으니 typeof 키워드를 이용해 조건 분기를 해주면 에러응 없앨 수 있다
          a.toFixed(1);
        }
      }
    },
    mounted(){
      // 타입 추론
      let name = "Lee Eun Seok"; // name은 string이라는 추론이 일어나서 자동으로 넣어준다(name:string)

      // 타입 단언
      let btnText = document.querySelector(".add-text") as HTMLElement;   // as HTMLElement를 넣어서 명시적으로 형변환해준다(넣지않으면 타입스크립트가 적절한 타입을 찾지못해 오류가 발생한다)
      btnText.addEventListener("click", (evt)=> {
        this.addText(evt, name);
      });

      this.numOrStr(1);
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
    cursor: pointer;
  }
  .add-text {
    margin:30px auto 0;
    width:150px;
    height:30px;
    display:block;
    border: 1px solid #000;
    cursor: pointer;
  }
</style>
