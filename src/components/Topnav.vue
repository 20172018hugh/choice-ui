<template>
    <div class="topnav">
        <div class="logo" @click="toggleMenu">LOGO</div>
        <ul class="menu">
            <li>菜单1</li>
            <li>菜单2</li>
        </ul>
    </div>
</template>
<script lang="ts">
import { inject, Ref } from 'vue'
export default {
    name: 'Topnav',
    setup() {
        const menuVisiable = inject<Ref<boolean>>('menuVisiable');
        console.log('topnav的inject值:', menuVisiable.value);
        const toggleMenu = () => {
            menuVisiable.value = !menuVisiable.value
        }
        return {
            toggleMenu,
            menuVisiable,
        }
    }
}
</script>
<style lang="scss" scoped>
.topnav {
    background: pink;
    display: flex;
    padding: 16px;
    position: relative;
    justify-content: center;
    align-items: center;
    z-index: 10;

    >.logo {
        max-width: 6em;
        margin-right: auto;
    }

    >.menu {
        display: flex;
        white-space: nowrap;
        flex-wrap: nowrap;

        >li {
            margin: 0 1em;
        }
    }

    @media (max-width: 500px) {
        >.menu {
            display: none
        }

        >.logo {
            margin: 0 auto
        }
    }
}
</style>