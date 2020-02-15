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
  import TestReactive from './TestReactive'
  import TestSetup from './TestSetup'
  import TestLogicReuse from './TestLogicReuse'
  

  export default {
    components: {TestRef, TestReactive, TestSetup, TestLogicReuse},
    setup() {
      const routes = [
        {name: 'setup', component: 'TestSetup'},
        {name: 'reactive', component: 'TestReactive'},
        {name: 'ref', component: 'TestRef'},
        {name: 'logicReuse', component: 'TestLogicReuse'},
      ]
      const activeCom = ref(routes[0].name)
      const onClick = (r) => {
        activeCom.value = r.name
      }

      return {routes, activeCom, onClick};
    }
  }
</script>
<style lang="less" scoped>
  .main {
    padding: 0 30px;
    &-ul {
      padding: 0;
      
      .li {
        display: inline-block;
        margin-right: 20px;
        cursor: pointer;
      }
      .active {
        color: #00f;
      }
    }
  }
</style>