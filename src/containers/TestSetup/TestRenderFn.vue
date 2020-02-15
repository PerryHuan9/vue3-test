<script>
import {reactive, h, ref} from 'vue'

export default {
  setup() {
    const state = reactive({msg: 'setup使用renderFn'})
    return () => h('div', [
      '2.',
      state.msg,
      h('pre',{class: 'code-bg'} ,[
  `
  \<script\>
  import {reactive, h, ref} from 'vue'

  export default {
    setup() {
      const state = reactive({msg: 'setup使用renderFn'})
      return () => h('div', [
        '2.',
        state.msg,
      ])
    }
  }
  \</script\>
  `
      ])
     ])
  }
}
</script>