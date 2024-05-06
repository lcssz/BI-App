<template>
    <router-link :to="to" class="link" :class="{ active: isActive }">
      <i class="icon" :class="icon" />
      <span v-show="!isCollapsed"><slot/></span>
    </router-link>
  </template>
  
  <script>
  import {defineComponent, computed} from 'vue'
  import {useRoute} from 'vue-router'
  
  export default defineComponent({
      name: 'SideBarLink',
      props: {
          to: { type: String, required: true },
          icon: { type: String, required: true },
          isCollapsed: { type: Boolean, required: true }
      },
      setup(props){
          const route = useRoute();
          const isActive = computed(() => route.path === props.to);
          return {isActive}
      }
  })
  </script>
  
  <style scoped>
  .link {
    display: flex;
    align-items: center;
    position: relative;
    cursor: pointer;
    font-size: 16px;
    font-family: "Nunito", sans-serif;
    font-optical-sizing: auto;
    font-weight: 600;
    font-style: normal;
  
    margin: 0.1em 0;
    padding: 0 0 0 2em;
  
    height: 3em;
  
    color: var(--sidebar-item-color);
    mix-blend-mode: normal;
    text-decoration: none;
  }
  .link.active {
    background: linear-gradient(to left,transparent 80%,var(--sidebar-item-bg-gradient));
    color: var(--sidebar-item-select)
  }
  .link .icon {
    flex-shrink: 0;
    width: 30px;
    margin-right: 10px;
  }
  </style>