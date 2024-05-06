<template>
    <div class="sidebar" :style="{width: sidebarWidth, margin: sidebarMargin, borderRadius:borderRadius}" @mouseover="toggleSideBar" @mouseout="toggleSideBar">
        <img v-show="!isCollapsed" src="../assets/logo_brasilinspecao.png" class="logo"/>
        <SideBarLink :isCollapsed="isCollapsed" to="/" icon="fa-solid fa-house">Home</SideBarLink>
        <SideBarLink :isCollapsed="isCollapsed" to="/dashboard" icon="fa-solid fa-square-poll-vertical">Dashboard</SideBarLink>
    </div>
</template>

<script>
    import {ref, computed, defineComponent} from 'vue'
    import SideBarLink from './SideBarLink.vue';

    const isCollapsed = ref(true)
    const toggleSideBar = () => (isCollapsed.value = !isCollapsed.value);
    // Calculate width 
    const SIDEBAR_WIDTH = 215
    const SIDEBAR_WIDTH_COLLAPSED = 80
    const sidebarWidth = computed(() => `${isCollapsed.value? SIDEBAR_WIDTH_COLLAPSED : SIDEBAR_WIDTH}px`)

    // Calculate margin
    const SIDEBAR_MARGIN = 0
    const SIDEBAR_MARGIN_COLLAPSED = 30
    const sidebarMargin = computed(()=> `${isCollapsed.value? SIDEBAR_MARGIN_COLLAPSED : SIDEBAR_MARGIN}px`)

    // Calculate borderRadius
    const SIDEBAR_BORDER_RADIUS = 0
    const SIDEBAR_BORDER_RADIUS_COLLAPSED = 10
    const borderRadius = computed(()=> `${isCollapsed.value? SIDEBAR_BORDER_RADIUS_COLLAPSED : SIDEBAR_BORDER_RADIUS}px`)

    export default defineComponent({
    name:"SideBar",
    components: {
        SideBarLink
    },

    setup() {
        return {
            toggleSideBar,
            sidebarWidth,
            sidebarMargin,
            borderRadius,
            isCollapsed
        }
    },
})
</script>

<style scoped>
    .sidebar{
        color:white;
        background-color: var(--sidebar-bg-color);
        float: left;
        position: fixed;
        top: 0;
        left: 0;
        bottom: 0;
        transition: 0.4s ease;
        display: flex;
        flex-direction: column;
    }
    .logo{
        margin-top: 10px;
        margin-bottom: 10px;
        padding: 20px 0 60px;
        object-fit: cover;
    }
</style>
