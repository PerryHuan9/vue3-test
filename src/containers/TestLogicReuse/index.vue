<template>
  <div>
   <p> {{count}}</p>
    <button @click="onClick" :disabled="state">Start</button>  
  </div>
</template>

<script>
  import {ref} from 'vue'

  const useCountdown = (initialCount) => {
    const count = ref(initialCount)
    const state = ref(false)
    const start = (initCount) => {
      state.value = true;
      if (initCount > 0) {
        count.value = initCount
      } 
      if (!count.value) {
        count.value = initialCount
      }
      const interval = setInterval(() => {
        if (count.value === 0) {
          clearInterval(interval)
          state.value = false
        } else {
          count.value--
        }
      }, 1000)
    }
    return {
      count,
      start,
      state
    }
  }

  export default {
   setup() {
     const {count, start, state} = useCountdown(10)
     const onClick = () => {
        start()
     }
     return  {count, onClick, state}
   }
  }

</script>