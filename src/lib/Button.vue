<template >
    <div :size="size">
        <button v-bind="rest">
            <slot />
        </button>
    </div>
</template>
<script lang="ts">
export default {
    inheritAttrs: false,//默认不继承属性
    // 实现属性分别绑定，按需绑定
    setup(props, context) {
        const { size, ...rest } = context.attrs;
        return {
            size,
            rest,
        }
    }
}
</script>
<style lang="">
    
</style>