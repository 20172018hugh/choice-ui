<template>
    <div>Button示例</div>
    <h1>示例1</h1>
    <Button @click="onClick">你好</Button>
</template>
<script>
import Button from '../lib/Button.vue'
export default {
    name: "ButtonDemo",
    components: { Button },
    setup() {
        const onClick = () => {
            console.log('点击了button')
        }
        return {
            onClick,
        }
    }
}
</script>
<style lang="">
    
</style>