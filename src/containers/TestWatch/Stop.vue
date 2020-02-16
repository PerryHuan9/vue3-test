<template>
  <div>
     <h3>Stop watch</h3>
    <input type="text" v-model="inputRef">
    <button @click="onClick">stop</button>
  </div>
</template>

<script>
  import {watch, ref} from 'vue'

  export default {
    setup() {
      const inputRef = ref('')
      const stop = watch(() => {
        console.log('watch', inputRef.value)
      })
      const onClick = () => {
        // 取消watch
        stop()
      }
      return {inputRef, onClick}
    }
  }
</script>