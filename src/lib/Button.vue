<template >
    <button class="choice-button" :class="classes">
        <slot />
    </button>
</template>
<script lang="ts">import { computed } from 'vue';

export default {
    // inheritAttrs: false,//默认不继承属性
    // 实现属性分别绑定，按需绑定
    props: {
        theme: { type: String, default: 'button' },
        size: { type: String, default: 'normal' },
        level: { type: String, defatul: 'normal' },
    },
    setup(props) {
        // const { size, ...rest } = context.attrs;
        // return {
        //     size,
        //     rest,
        // }
        const classes = computed(() => ({
            [`choice-theme-${props.theme}`]: props.theme,
            [`choice-size-${props.size}`]: props.size,
            [`choice-level-${props.level}`]: props.level,
        }))
        return {
            classes,
        }
    }
}
</script>
<style lang="scss">
$h: 32px;
$border-color: #d9d9d9;
$color: #333;
$blue: #40a9ff;
$radius: 4px;
$red: #f56c6c;

.choice-button {
    box-sizing: border-box;
    height: $h;
    padding: 0 12px;
    cursor: pointer;
    display: inline-flex;
    justify-content: center;
    align-items: center;
    white-space: nowrap;
    background: white;
    color: $color;
    border: 1px solid $border-color;
    border-radius: $radius;
    box-shadow: 0 1px 0 fade-out(black, 0.95);
    transition: background 250ms;

    &+& {
        margin-left: 8px;
    }

    &:hover,
    &:focus {
        color: $blue;
        border-color: $blue;
    }

    &:focus {
        outline: none;
    }

    &::-moz-focus-inner {
        border: 0;
    }

    &.choice-theme-link {
        border-color: transparent;
        box-shadow: none;
        color: $blue;

        &:hover,
        &:focus {
            color: lighten($blue, 10%);
        }
    }

    &.choice-theme-text {
        border-color: transparent;
        box-shadow: none;
        color: inherit;

        &:hover,
        &:focus {
            background: darken(white, 5%);
            ;
        }
    }

    &.choice-size-big {
        font-size: 24px;
        height: 48px;
        padding: 0 16px
    }

    &.choice-size-small {
        font-size: 12px;
        height: 20px;
        padding: 0 4px;
    }

    &.choice-theme-button {
        &.choice-level-main {
            background: $blue;
            color: white;
            border-color: $blue;

            &:hover,
            &:focus {
                background: darken($blue, 10%);
                border-color: darken($blue, 10%);
            }
        }

        &.choice-level-danger {
            background: $red;
            border-color: $red;
            color: white;

            &:hover,
            &:focus {
                background: darken($red, 10%);
                border-color: darken($red, 10%);
            }
        }
    }

    &.choice-theme-link {
        &.choice-level-danger {
            color: $red;

            &:hover,
            &:focus {
                color: darken($red, 10%);
            }
        }
    }

    &.choice-theme-text {
        &.choice-level-main {
            color: $blue;

            &:hover,
            &:focus {
                color: darken($blue, 10%);
            }
        }

        &.choice-level-danger {
            color: $red;

            &:hover,
            &:focus {
                color: darken($red, 10%);
            }
        }
    }
}
</style>