<template>
  <div>
    <h4 >3. setup的第二个参数context</h4>  
    <input type="text" :value="modelValue" @input="onInput">{{modelValue}}
  </div>
  <pre class="code-bg">
    &lt;template&gt;
        &lt;div&gt;
          &lt;h4 &gt;3. setup的第二个参数context&lt;/h4&gt;  
          &lt;input type="text" :value="state.value" @input="onInput"&gt;
        &lt;/div&gt;
    &lt;/template&gt;
    &lt;script&gt;
      import {reactive, defineComponent} from 'vue'

      export default {
        props: {
          modelValue: String
        },
        setup(props, context) {
          const {modelValue} = props
          const onInput = (e) =&gt; {
            context.emit('update:modelValue', e.srcElement.value)
          }
          return {modelValue, onInput}
        }
      }
    &lt;/script&gt;
  </pre>
</template>
<script>
  import {reactive, defineComponent, toRefs, onRenderTracked, onRenderTriggered} from 'vue'

  export default {
    props: {
      modelValue: String
    },
    setup(props, context) {
      // onRenderTracked(() => {
      //   debugger;
      // })
      // onRenderTriggered(() => {
      //   debugger;
      // })
      const onInput = (e) => {
        context.emit('update:modelValue', e.srcElement.value)
      }
      return {...toRefs(props), onInput}
    }
  }
</script>