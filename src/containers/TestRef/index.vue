<template>
  <div class="tf">
    <h3>Test Ref</h3>
    <input type="text" v-model="value">
    {{value}}
    <p>{{newValue}}</p>
    <div>
      <p>{{count}}</p>
      <button @click="onClick(true)">+</button>
      <button @click="onClick(false)">-</button>
    </div>
  </div>
</template>
<script>
  import {ref} from 'vue'

  export default {
    setup() {
      const value = ref('')
      const count = ref(0)
      const onClick = (isAdd) => {
        isAdd ? count.value++ : count.value -- 
      }
      const objRef = ref({a: 1213})
      console.log(objRef.value)
      return {
        value,
        count,
        onClick,
      }
    },
    computed: {
      newValue() {
        return 'newValue:'+this.value
      }
    },
  }
</script>
<style lang="css" scoped>
  .tf {
    margin-top: 30px;
  }

</style>


