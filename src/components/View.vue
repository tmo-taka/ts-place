<script setup lang="ts">
import Export from './Export.vue';
import { defineExpose, PropType  } from 'vue';
import { Define } from '@/types/define';

  // 型推論が有効になります
interface Props {
    msg?: PropType<String>,
    obj:  PropType<Define>,
}

const props = withDefaults(defineProps<Props>(),{
  // なんでこれでないといけないのかがわからない？
  msg: () => 'これがデフォルト値か>',
})

class MemberList{

  lists: array;

  constructor(lists:array) {
    this.lists = lists
  }
  lookHeight(): void {
    for(let obj of this.lists){
      console.log(obj.name + ':' + obj.height)
    }
  }
  lookWeight() :void {
    for(let obj of this.lists){
      console.log(obj.name + ':' + obj.weight)
    }
  }
}

const memberList = new MemberList(
  [
    {name: 'yuki', height: '167cm', weight: '58kg'},
    {name: 'kota', height: '172cm', weight: '68kg'},
    {name: 'tetsu', height: '153cm', weight: '45kg'},
  ]
)

const testValue = props.msg
const test = "テスト";

defineExpose({test})
</script>

<template>
  <div>
    <div>{{msg}}</div>
    <div>{{obj.test}}</div>
    <div>これがProps代入：{{testValue}}</div>
    <button @click="memberList.lookWeight()">体重を見る</button>
    <Export />
  </div>
</template>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
