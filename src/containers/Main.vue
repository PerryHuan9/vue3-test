<template>
  <main class="main">
    <ul class="main-ul">
      <template v-for="r in routes">
        <li :key="r.name" @click="onClick(r)" :class="['li', activeCom === r.name ? 'active': '']">
         {{r.name}}
        </li>
      </template>
    </ul>
    <template  v-for=" r in routes">
     <component :is="r.component" :key="r.name" v-if="r.name === activeCom" />
    </template>
  </main>
</template>
<script>
  import {ref} from 'vue'
  import TestRef from './TestRef'

  export default {
    components: {TestRef},
    setup() {
      const routes = [
        {name: 'ref', component: 'TestRef'}
      ]
      const activeCom = ref(routes[0].name)
      const onClick = (r) => {
        activeCom.value = routes.component
      }
      
      return {routes, activeCom};
    }
  }
</script>
<style lang="less" scoped>
  .main {
    padding: 0 30px;
    &-ul {
      padding: 0;
      
      .li {
        display: inline-block
      }
      .active {
        color: #00f;
      }
    }
  }
</style>