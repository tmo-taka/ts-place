<template>
  <div>{{msg}}</div>
  <div>{{obj.test}}</div>
</template>

<script lang="ts">
import { defineComponent, PropType  } from 'vue';
import { define } from '@/types/define';

export default defineComponent({
  // 型推論が有効になります
  props: {
    msg: {
      type: String,
    },
    obj : Object as PropType<define>
  }
})
</script>

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
