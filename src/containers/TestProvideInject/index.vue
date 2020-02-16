<template>
  <div>
    <h3>父组件</h3>
    {{themtState}}
    <input type="text" v-model="themtState.color">
  </div>
  <Descendent />
</template>
<script>
  import { provide, reactive } from 'vue'
  import {ThemeSymbol} from './symbol'
  import Descendent  from './Descendent'

  export default {
    components: {Descendent},
    setup() {
      const themtState = reactive({color: 'red'})
      provide(ThemeSymbol, themtState)
      return {themtState}
    }
  }

</script>