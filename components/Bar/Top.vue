<template>
    <v-app-bar :elevation="5" color="primary" density="compact">
        <template v-slot:prepend>
            <v-app-bar-nav-icon></v-app-bar-nav-icon>
        </template>

        <v-app-bar-title>myTVET</v-app-bar-title>

        <v-spacer></v-spacer>

        <v-btn icon>
            <v-icon>mdi-magnify</v-icon>
        </v-btn>

        <template v-slot:append>
            <v-btn icon="mdi-dots-vertical"></v-btn>
        </template>
    </v-app-bar>
</template>

<script setup>

</script>

<style lang="scss" scoped>

</style>