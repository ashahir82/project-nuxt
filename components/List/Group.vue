<template>
    <v-list-item
        v-for="institute in institutes"
        :title="institute.kursus"
        :value="institute.kursus"
    ></v-list-item>
</template>

<script setup>
    import axios from "axios";
    const props = defineProps(["pusat"]);
    const institutes = ref([]);
    const url = "http://mytevt-laravel.test/api/pusat-institusi";

    const apiPusatKursus = async () => {
        let data = {
            pusat: props.pusat,
        };

        const config = {
            headers: {
                Accept: "application/json",
            },
        };

        await axios.post(url, data, config).then((response) => {
            institutes.value = response.data.data;
        });
    };

    onBeforeMount(async() => {
        apiPusatKursus();
    });
</script>

<style lang="scss" scoped>

</style>