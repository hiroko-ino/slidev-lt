<template>
    <Progress
        v-if="$slidev.nav.currentPage !== 1 && $slidev.nav.currentLayout!== 'end'"
        :current="$slidev.nav.currentPage"
        :total="$slidev.nav.total" />
</template>