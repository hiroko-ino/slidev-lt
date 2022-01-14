<template>
    <div 
        v-if="isShow"
        v-motion
        :initial="{
            y: 50,
            opacity: 0
        }"
        :enter="{
            y: 0,
            opacity: 1,
            transition: {
                y: {
                    duration: 300
                    }
                }
            }">
        <slot />
    </div>
</template>

<script lang="ts">
    export default {
        name: "Fadein",
        props: {
            currentPage: {
                type: Number,
                default: 0,
                required: true
            },
            index: {
                type: Number,
                default: 0,
                required: true
            }
        },
        computed: {
            isShow() {
                return this.currentPage === this.index
            }
        }
    };
</script>