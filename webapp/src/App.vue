<template>
  <main id="app">
    <SideBar/>
    <div>
      <router-view />
    </div>
    </main>
</template>

<script>
  import SideBar from './components/SideBar.vue'
  import {defineComponent} from 'vue'
  export default defineComponent({
    components: {
      SideBar
    },
    setup() {
    }
  })
</script>

<style>
:root {
  @import url('https://fonts.googleapis.com/css2?family=Nunito:ital,wght@0,200..1000;1,200..1000&display=swap');
  --sidebar-bg-color: #ffffff;
  --sidebar-item-color: #9a9ba8;
  --sidebar-item-select: #3A974C;
  --sidebar-item-bg-gradient:hsla(132, 44%, 41%, 0.3);
  --bg-color: #FAFAFB;
}
body{
  background-color: var(--bg-color);
}
</style>