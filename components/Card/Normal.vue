<template>
    <v-card class="mx-auto" prepend-icon="$vuetify" :subtitle="subtitle" hover>
        <template v-slot:title>
            <span class="font-weight-black">{{ title }}</span>
        </template>

        <v-card-text class="bg-surface-light pt-4">
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Commodi, ratione debitis quis est labore voluptatibus! Eaque cupiditate minima, at placeat totam, magni doloremque veniam neque porro libero rerum unde voluptatem!
        </v-card-text>
        <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn>Click me</v-btn>
        </v-card-actions>
    </v-card>
</template>

<script setup>
    const props = defineProps({
        title: String,
        subtitle: String
    });
</script>

<style lang="scss" scoped>

</style>