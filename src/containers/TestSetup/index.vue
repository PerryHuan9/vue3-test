<template>
<div>
  <div>
    1. {{state.msg}}
  </div>
  <pre class="code-bg">
    &lt;template&gt;
      &lt;div&gt;
        {{state.msg}}
      &lt;/div&gt;
      &lt;TestRenderFn/&gt;
    &lt;/template&gt;  


    &lt;script&gt;
      import {reactive} from 'vue'
      import TestRenderFn from './TestRenderFn'

      export default {
        components: {TestRenderFn},
        setup() {
          const state = reactive({
            msg: '返回state在template中使用'
          })
          return {state}
        }
      }
    &lt;/script&gt;
  </pre>
  <TestRenderFn/>
  <TestContext v-model="state.testContext"/>{{state.testContext}}
  <button @click="onClick">改变</button>  
  </div>
</template>   


<script>
import {reactive} from 'vue'
import TestRenderFn from './TestRenderFn'
import TestContext from './TestContext'

export default {
  components: {TestRenderFn, TestContext},
  setup() {
    const state = reactive({
      msg: '返回state在template中使用',
      testContext: '12313'
    })
    const onClick = () => {
      state.testContext = '123123'
    }
    return {state, onClick}
  }
}
</script>




