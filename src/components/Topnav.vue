<template>
    <div class="topnav">
        <div class="logo">LOGO</div>
        <ul class="menu">
            <li>菜单1</li>
            <li>菜单2</li>
        </ul>
        <span class="toggleAside" @click="toggleMenu"></span>
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
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
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

    >.toggleAside {
        display: none;
        width: 24px;
        height: 24px;
        background: red;
        position: absolute;
        left: 16px;
        top: 50%;
        transform: translateY(-50%);
    }

    @media (max-width: 500px) {
        >.menu {
            display: none
        }

        >.logo {
            margin: 0 auto
        }

        >.toggleAside {
            display: inline-block;
        }
    }
}
</style>