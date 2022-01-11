<!-- hide the footer from Page 4 -->
<template>
    <Progress v-if="$slidev.nav.currentPage !== 1" v-bind:current="$slidev.nav.currentPage" />
</template>