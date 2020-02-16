<template>
  <div>
    state.count: <input type="text" v-model="state.count">{{state.count}}<br/><br/>
    inputRef: <input type="text" v-model="inputRef">{{inputRef}}<br/><br/>

    state2.count: <input type="text" v-model="state2.count">{{state2.count}}<br/><br/>
    ref2: <input type="text" v-model="ref2">{{ref2}}<br/><br/>
  </div>
  <Multi />
  <Stop />
  <Cleanup />
  <Option />
</template>
<script>
  import {watch, reactive, ref} from 'vue'
  import Multi from './Multi'
  import Stop from './Stop'
  import Cleanup from './Cleanup'
  import Option from './Option'

  export default {
    components: {Multi,Stop, Cleanup, Option},
    setup() {
      const state = reactive({count: 0})
      const inputRef = ref('')
      // state.count与inputRef中任意一个源改变都会触发watch
      watch(() => {
        console.log('state', state.count)
        console.log('ref', inputRef.value)
      })

      const state2 = reactive({count: ''})
      const ref2 = ref('')
      watch(
        () => state2.count,
        (curVal, preVal) => {
          console.log('state2.count',state2.count)
          console.log('ref2.value',ref2.value)
      })
      watch(ref2, (curVal, preVal) => {
        console.log('state2.count',state2.count)
        console.log('ref2.value',ref2.value)
      })

      return {state, inputRef, state2, ref2}
    }
  }
</script>
