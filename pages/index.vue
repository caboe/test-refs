<template>
  <div class="hello">
   <div v-for="(item, idx) in list" :ref="setItemRef" :key="idx">foo {{ idx }}</div>
  </div>
</template>

<script>
import { onBeforeUpdate, onUpdated, onMounted } from '@nuxtjs/composition-api'

export default {
  setup() {
    let itemRefs = []
    let list = [1,2,3]
    const setItemRef = el => {
      console.log(el);
      if (el) {
        itemRefs.push(el)
      }
    }
    onBeforeUpdate(() => {
      itemRefs = []
    })
    onUpdated(() => {
      console.log(itemRefs)
    })
    onMounted(() => {
      console.log('itemRefs', itemRefs);
    })
    return {
      setItemRef,
      list
    }
  }
}
</script>
