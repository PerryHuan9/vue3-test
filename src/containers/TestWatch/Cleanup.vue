<template>
  <div>
    <h3>Cleanup</h3>
    <input type="text" v-model="inputRef">
    <input type="text" v-model="inputRef2">
  </div>
</template>

<script>
  import {ref, watch} from 'vue'

  export default {
    setup() {
      const inputRef = ref('')
      const getData = (value) => {
        const handler = setTimeout(() => {
            console.log('已获得数据', value)
        }, 5000)
        return handler
      }
      watch((onCleanup) => {
        const handler = getData(inputRef.value)
        // 清除副作用
        onCleanup(() => {
          clearTimeout(handler)
        })
      })

      // 另外一种获取onCleanup的方式
      const inputRef2 = ref('')
      watch(inputRef2, (val, oldVal, onCleanup) => {
        const handler = getData(val)
        // 清除副作用
        onCleanup(() => {
          clearTimeout(handler)
        })
      })

      return {inputRef, inputRef2}
    }
  }
</script>