<template>
  <div>
    <input type="text" v-model="state.input">
    <p>input: {{state.input}}</p> 
    <p>computedInput: {{state.computedInput}}</p> 
    <p>singleComputed: {{singleComputed}}</p> 
  </div>
</template>
<script>
  import {reactive, computed, watch} from 'vue'

  export default {
    setup(props) {
      const state = reactive({
        input: '', 
        computedInput: computed(() => '$$  '+state.input+'  $$' )
      })
      const singleComputed = computed(() => '%%  '+state.input+'  %%')
      watch(() => {

      })
      return {state, singleComputed}
    }
  }
</script>