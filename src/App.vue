<template>
  <router-view />
</template>

<script lang="ts">
import { provide, ref } from 'vue';
import { router } from './router'
export default {
  name: 'App',
  setup() {
    //
    const width = document.documentElement.clientWidth;
    const menuVisiable = ref(width <= 500 ? false : true);
    provide('menuVisiable', menuVisiable)
    router.afterEach(() => {
      if (width <= 500) {
        menuVisiable.value = false;
      }
    })
  }
}
</script>