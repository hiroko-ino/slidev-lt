<!-- hide the footer from Page 4 -->
<template>
    <Progress
        v-if="$slidev.nav.currentPage !== 1"
        :current="$slidev.nav.currentPage"
        :total="$slidev.nav.total" />
</template>