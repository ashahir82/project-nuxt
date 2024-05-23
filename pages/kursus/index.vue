<template>
    <v-layout>
        <BarTop />

        <v-main>
            <v-container>
                <HeaderMain title="Senarai Kursus TVET" />

                <v-card class="mb-3">
                    <v-card-text>Carian</v-card-text>
                </v-card>

                <v-list lines="two">
                    <v-list-item v-for="course in courses" :key="course.id" :subtitle="course.pusat" :title="course.kursus">
                        <template v-slot:prepend>
                            <v-avatar color="grey-lighten-1">
                                <v-icon color="white">mdi-folder</v-icon>
                            </v-avatar>
                        </template>

                        <template v-slot:append>
                            <v-btn
                                color="grey-lighten-1"
                                icon="mdi-information"
                                variant="text"
                            ></v-btn>
                        </template>
                    </v-list-item>
                </v-list>
            </v-container>

            <v-pagination v-model="page" :length="pages" :total-visible="3"></v-pagination>
        </v-main>

        <BarBottom menu="2" />
    </v-layout>
</template>

<script setup>
    import axios from "axios";
    const url = "http://mytevt-laravel.test/api/senarai-kursus?page=";
    const courses = ref([]);
    const page = ref(1);
    const pages = ref(1);
    const dialog = ref(false);

    const apiKursus = async() => {
        await axios.get(url + page.value).then((response) => {
            courses.value = response.data.data.data;
            pages.value = response.data.data.last_page;
        });
    };

    onBeforeMount(async() => {
        apiKursus(page.value);
    });

    watchEffect(page => {
        apiKursus(page.value);
    });
</script>

<style lang="scss" scoped>

</style>