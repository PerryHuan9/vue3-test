<template>
  <div>
    <h3>子组件</h3>
    {{theme}}
  </div>
</template>

<script>
  import {inject} from 'vue'
  import {ThemeSymbol} from './symbol'

  export default {
    setup() {
      const theme = inject(ThemeSymbol, {color: 'blue'} /**默认值 */)
      return {theme}
    }
  }
</script>
