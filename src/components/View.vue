<script setup lang="ts">
import { defineProps, PropType  } from 'vue';
import { define } from '@/types/define';

  // 型推論が有効になります
const props = defineProps({
    msg: String,
    obj : Object as PropType<define>
})

const testValue = props.msg
</script>

<template>
  <div>{{msg}}</div>
  <div>{{obj.test}}</div>
  <div>これがProps代入：{{testValue}}</div>
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
