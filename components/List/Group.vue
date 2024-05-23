<template>
    <v-list-item
        v-for="institute in institutes"
        :key="institute.id"
        :title="institute.kursus"
        :value="institute.kursus"
        prepend-icon="mdi mdi-hammer-wrench"
    ></v-list-item>
</template>

<script setup>
    import axios from "axios";
    const props = defineProps(["pusat"]);
    const institutes = ref([]);
    const url = "http://mytevt-laravel.test/api/pusat-institusi";

    onBeforeMount(async () => {
        let data = {
            pusat: props.pusat,
        };

        const config = {
            headers: {
                Accept: "application/json",
                Authorization: "Bearer " + localStorage.getItem("token"),
            },
        };

        await axios.post(url, data, config).then((response) => {
            institutes.value = response.data.data;
        });
    });
</script>

<style lang="scss" scoped>

</style>