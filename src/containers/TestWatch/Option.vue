<template>
  <div>
     <h3>Watch Option</h3>

     <h4>test lazy</h4>
    <input type="text" v-model="inputRef">

    <h4>test deep</h4>
    <button @click="onClick">changeRef</button>

    <h4>test onTrigger & onTrack</h4>
    <input type="text" v-model="debugRef">

    <h4>test flush</h4>
    <input type="text" v-model="flushRef">
  </div>
</template>
<script>
  import {watch, ref, reactive} from 'vue'

  export default {
    setup() {
      const inputRef = ref('')
      // 配置lazy为true之后，组件挂载不会执行，知道inputRef改变才执行
      watch(() => {
        console.log(inputRef.value)
      }, {lazy: true})

      const objRef = ref({a: {b: 123}, c: 123})
      watch(objRef,() => {
        console.log('objRef.value.a.b',objRef.value.a.b)
      }, {deep: true})
      const onClick = () => {
        objRef.value.a.b = 780
      }

      // 在组件挂载之后只有onTrack被调用
      // 在debugRef改变之后先调用onTrigger，再调用onTrack
      const debugRef = ref(0)
      watch(() => {
        console.log('debugRef.value:',debugRef.value)
      }, {
        onTrack() {
          debugger;
        },
        onTrigger() {
          debugger;
        }
      })

      const flushRef= ref('ad')
      watch(() => {
        console.log('flushRef.value: ', flushRef.value)
      }, {flush: 'pre'})

      return {inputRef, onClick, debugRef, flushRef}
    }
  }
</script>