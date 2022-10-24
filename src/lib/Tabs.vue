<template >
    <div class="choice-tabs">
        <div class="choice-tabs-nav" ref="container">
            <div class="choice-tabs-nav-item" v-for="(t,index) in titles" :key="index" @click="select(t)"
                :class="{selected: t=== selected}" :ref="el => { if (el) navItems[index] = el }">{{t}}
            </div>
            <div class="choice-tabs-nav-indicator" ref="indicator"></div>
        </div>
        <div class="choice-tabs-content">
            <component class="choice-tabs-content-item" :is="current" :key="current"></component>
        </div>
    </div>
</template>
<script lang="ts">
import Tab from './Tab.vue'
import { computed, onMounted, onUpdated, ref } from 'vue'
export default {
    props: {
        selected: {
            type: String,
        }
    },
    setup(props, context) {
        const defaults = context.slots.default()
        const navItems = ref<HTMLDivElement[]>([])
        const indicator = ref<HTMLDivElement>(null)
        const container = ref<HTMLDivElement>(null)
        defaults.forEach((tag) => {
            if (tag.type !== Tab) {
                throw new Error('Tabs 子标签必须是 Tab')
            }
        })
        const titles = defaults.map((tag) => {
            return tag.props.title
        })
        const current = computed(() => {
            return defaults.find((tag) => tag.props.title === props.selected
            )
        })
        const select = (title: string) => {
            context.emit('update:selected', title)
        }
        const x = () => {
            const divs = navItems.value
            const res = divs.find(div => div.classList.contains('selected'));
            const { width } = res.getBoundingClientRect()
            indicator.value.style.width = width + 'px';
            const { left: left1 } = container.value.getBoundingClientRect()
            const { left: left2 } = res.getBoundingClientRect()
            indicator.value.style.left = (left2 - left1) + 'px'
        }
        onMounted(x)
        onUpdated(x)
        return {
            defaults,
            titles,
            current,
            select,
            navItems,
            indicator,
            container,
        }
    }

}
</script>
<style lang="scss">
$blue: #40a9ff;
$color: #333;
$border-color: #d9d9d9;

.choice-tabs {
    &-nav {
        display: flex;
        color: $color;
        border-bottom: 1px solid $border-color;
        position: relative;

        &-item {
            padding: 8px 0;
            margin: 0 16px;
            cursor: pointer;

            &:first-child {
                margin-left: 0;
            }

            &.selected {
                color: $blue;
            }
        }

        &-indicator {
            position: absolute;
            height: 3px;
            background: $blue;
            left: 0;
            bottom: -1px;
            transition: all 250ms;
        }
    }

    &-content {
        padding: 8px 0;
    }
}
</style>