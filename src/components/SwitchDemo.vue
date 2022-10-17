<template>
    <div>
        <Switch :checked="checked" v-model:checked="checked" />
    </div>
</template>
<script>
import Switch from '../lib/Switch.vue'
import { ref } from 'vue'
export default {
    name: 'SwitchDemo',
    components: {
        Switch
    },
    setup() {
        const checked = ref(false)
        return {
            checked,
        }
    }
}
</script>
<style lang="">
    
</style>