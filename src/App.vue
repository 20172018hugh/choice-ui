<template>
  <router-view />
</template>

<script lang="ts">
import { provide, ref } from 'vue';
export default {
  name: 'App',
  setup() {
    //
    const width = document.documentElement.clientWidth;
    const menuVisiable = ref(width <= 500 ? false : true);
    provide('menuVisiable', menuVisiable)
  }
}
</script>