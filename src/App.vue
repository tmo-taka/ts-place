
<script setup lang="ts">
  const msg = 'Hello TypeScript'
</script>

<template>
  <div>
    <img alt="Vue logo" src="./assets/logo.png">
    <View msg="Welcome to Your Vue.js + TypeScript App" :obj="obj"/>
    <div>あああ</div>
    <button @click="changeFlag(true)">{{flag}}</button>
    <div>{{msg}}</div>
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive } from 'vue';
import View from './components/View.vue';
import { define } from '@/types/define';

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
        } as define,
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
