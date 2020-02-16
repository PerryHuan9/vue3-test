<template>
  <div ref="root">
    Test Template Refs
  </div>
</template>

<script>
import { ref, onMounted } from 'vue'

export default {
  setup() {
    const root = ref(null)

    onMounted(() => {
      // 在render初始化之后，DOM元素将被赋值为ref
      console.log(root.value) // div dom对象
    })

    return {
      root
    }
  }
}
</script>