<template>
    <div>Button示例</div>
    <h1>示例1</h1>
    <div>
        <Button @click="onClick" theme="text">你好</Button>
        <Button @click="onClick" theme="button">你好</Button>
        <Button @click="onClick" theme="link">你好</Button>
        <Button @click="onClick">你好</Button>
    </div>
    <h1>示例2</h1>
    <div>
        <Button size="small">你好</Button>
        <Button>你好</Button>
        <Button size="big">你好</Button>
    </div>
</template>
<script>
import Button from '../lib/Button.vue'
export default {
    name: "ButtonDemo",
    components: { Button },
    setup() {
        const onClick = () => {
            console.log('hi')
        }
        return {
            onClick,
        }
    }
}
</script>
<style lang="">
    
</style>