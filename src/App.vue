
<script setup lang="ts">
  let msg = ref<string>('Hello TypeScript');
  const changeMsg = '変わったべ';

  interface State {
    inputValue: string;
  }

  let {inputValue} = toRefs(reactive<State>({
    inputValue: '',
  }))
  let inputValue2 = ref('テスト')

  const changeMessage = () => {
    console.log(9);
    //valueに上書きしないとデータは変更されない
    msg.value = changeMsg
  }

  const childRef = ref();
  onMounted(() => {
    console.log(childRef.value);
  });
</script>

<template>
  <div>
    <img alt="Vue logo" src="./assets/logo.png">
    <View :obj="obj"/>
    <div>あああ</div>
    <button @click="changeFlag(true)">{{flag}}</button>
    <input type="text" v-model="inputValue">
    <div>{{msg}}</div>
    <div>入力されたもの:{{inputValue}}</div>
    <input type="text" v-model="inputValue2">
    <div>入力されたもの:{{inputValue2}}</div>
    <button @click="changeMessage()">文言帰る</button>
    <div>testValueの値{{childRef}}</div>
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive, toRefs, ref, onMounted  } from 'vue';
import View from './components/View.vue';
import { Define } from '@/types/define';

export default defineComponent({
  // 型推論が有効になります
  components: {
    View
  },
  data(){
    return {
        obj: {
          test: "これはテスト",
          flag: true,
          judge: '02',
        } as Define,
        flag: <boolean>false,
    };
  },
  methods: {
    changeFlag(judge: boolean): boolean{
      this.flag = judge
      return judge
    }
  }
})
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
