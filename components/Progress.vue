<template>
    <div class="absolute z-50 bottom-5 left-0 right-0 flex justify-center">
        <div class="w-50 relative h-1 bg-green-500/50 rounded-full overflow-hidden">
            <span class="absolute h-full bg-gray-500 transition-all duration-300" :style="style"></span>
        </div>
    </div>
</template>

<script lang="ts">
    export default {
        name: "Progress",
        props: {
            current: {
                type: Number,
                default: 0,
                required: true
            },
            total: {
                type: Number,
                default: 0,
                required: true
            },
        },
        computed: {
            style() {
                return {
                    width: `${100 / (this.total - 1)}%`,
                    left: `${100 / (this.total - 1) * (this.current - 2)}%`,
                }
            }
        }
    };
</script>