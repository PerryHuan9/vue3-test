<template>
  <input type="text" v-model="state.count">
  <button @click="onClick">change</button>
</template>
<script>
  import {reactive, readonly, watch} from 'vue'

  export default {
    setup() {
      const state = reactive({count: 12})
      const rnState = readonly(state)
      watch(() => {
        console.log(rnState.count)
      })

      const planObj = {count: 12}
      const rnPlanObj = readonly(planObj)
      const onClick = () => {
        planObj.count = 888
        console.log(rnPlanObj.count)
      }
      return {state, onClick}
    }
  }
</script>
