<script setup lang="ts">
import Export from './Export.vue';
import { defineExpose, PropType  } from 'vue';
import { define } from '@/types/define';

  // 型推論が有効になります
interface Props {
    msg?: PropType<String>,
    obj : PropType<define>
}

const props = withDefaults(defineProps<Props>(),{
  // なんでこれでないといけないのかがわからない？
  msg: () => 'これがデフォルト値か>',
})

const testValue = props.msg
const test = "テスト";

defineExpose({test})
</script>

<template>
  <div>
    <div>{{msg}}</div>
    <div>{{obj.test}}</div>
    <div>これがProps代入：{{testValue}}</div>
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
