<template>
    <v-bottom-navigation>
        <v-btn @click="home">
            <v-icon>mdi-television-play</v-icon>
            <span>Home</span>
        </v-btn>

        <v-btn @click="institusi">
            <v-icon>mdi-music-note</v-icon>
            <span>Institusi</span>
        </v-btn>

        <v-btn @click="kursus">
            <v-icon>mdi-book</v-icon>
            <span>Kursus</span>
        </v-btn>

        <v-btn @click="about">
            <v-icon>mdi-image</v-icon>
            <span>About</span>
        </v-btn>
    </v-bottom-navigation>
</template>

<script setup>
    const props = defineProps(["menu"]);
    const router = useRouter();

    const home = () => {
        router.replace("/");
    };
    const institusi = () => {
        router.replace("/institusi");
    };
    const kursus = () => {
        router.replace("/kursus");
    };
    const about = () => {
        router.replace("/utama/about");
    };
</script>

<style lang="scss" scoped>

</style>