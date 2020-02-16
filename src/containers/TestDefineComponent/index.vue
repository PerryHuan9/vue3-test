
<script>
import { defineComponent } from 'vue'

export default defineComponent({
  props: {
    foo: String
  },
  setup(props) {
    props.foo // <- type: string
  }
})
</script>