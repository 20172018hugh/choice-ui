<template>
    <button :class="{checked}" @click="toggle"><span></span></button>
</template>
<script lang="ts">
import { ref } from 'vue';

export default {
    name: 'Switch',
    props: {
        checked: {
            type: Boolean,
            default: false,
        }
    },
    setup(props, context) {
        const toggle = () => {
            context.emit('update:checked', !props.checked)
        }
        return {
            toggle,
        }
    }
}
</script>
<style lang="scss">
$h: 22px;
$h2: $h - 4px;

button {
    height: $h;
    width: $h*2;
    border: none;
    border-radius: $h/2;
    background: #bfbfbf;
    position: relative;

    >span {
        position: absolute;
        top: 2px;
        left: 2px;
        height: $h2;
        width: $h2;
        border-radius: $h2/2;
        background: white;
        transition: all 200ms;
    }

    &.checked {
        background: #1890ff;

        >span {
            left:calc(100% - #{$h2} - 2px)
        }
    }

    &:focus {
        outline: none;
    }

    &:active {
        >span {
            width: $h2 + 4px;
        }
    }

    &.checked:active {
        >span {
            width: $h2 + 4px;
            margin-left: -4px;
        }
    }
}
</style>