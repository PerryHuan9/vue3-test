<template>
  <div>
     <h3>多个依赖源</h3>
    <p>
      <input type="text" v-model="state.a"><br/><br/>
      <input type="text" v-model="state.b"><br/><br/>
    </p>
    <p>
      <input type="text" v-model="ref1"><br/><br/>
      <input type="text" v-model="ref2"><br/><br/>
    </p>
  </div>
</template>

<script>
  import {reactive, ref, watch} from 'vue'

  export default {
    setup() {
      const state = reactive({a: 'a', b: 'b'})
      watch(() => [state.a, state.b],
       ([a, b], [preA, preB]) => {
        console.log('callback params:', a, b, preA, preB)
        console.log('state.a', state.a)
        console.log('state.b', state.b)
        console.log('****************')
      })

      const ref1 = ref(1)
      const ref2 = ref(2)
      watch([ref1, ref2],([val1, val2], [preVal1, preVal2]) => {
        console.log('callback params:', val1, val2, preVal1, preVal2)
        console.log('ref1.value:',ref1.value)
        console.log('ref2.value:',ref2.value)
         console.log('##############')
      })
      return {state, ref1, ref2}
    }
  }
</script>