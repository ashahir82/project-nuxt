<template>
    <v-layout>
        <BarTop />

        <v-main>
            <v-container>
                <HeaderMain title="Senarai Kursus TVET" />

                <v-card v-for="course in courses.data" class="mb-3">
                    <v-card-text>
                        <h3 class="v-heading text-h6 text-sm-h5 text-lg-h4">{{ course.kursus }}</h3>
                        <p>Kursus di PB {{ course.pusat }}</p>
                    </v-card-text>
                    <v-card-actions>
                        <v-spacer></v-spacer>
                        <v-btn>Click me</v-btn>
                    </v-card-actions>
                </v-card>
            </v-container>

            <v-pagination v-model="page" :length="courses.last_page"></v-pagination>
        </v-main>

        <BarBottom menu="2" />

        <v-dialog v-model="dialog" width="auto">
            <v-card prepend-icon="mdi-update" title="Update in progress">
                <v-card-text>
                    <p>Your application will relaunch automatically after the update is complete.</p>
                </v-card-text>
                <v-divider></v-divider>

                <v-card-actions>
                    <v-spacer></v-spacer>
                    <v-btn text="Close" variant="plain" @click="dialog = false"></v-btn>
                    <v-btn color="primary" text="Save" variant="tonal" @click="dialog = false"></v-btn>
                </v-card-actions>
            </v-card>
        </v-dialog>
    </v-layout>
</template>

<script setup>
import axios from "axios";
    const url = "http://mytevt-laravel.test/api/senarai-kursus?page=";
    const courses = ref([]);
    const page = ref(1);
    const dialog = ref(false);

    const apiKursus = async() => {
        await axios.get(url + page.value).then((response) => {
            console.log("data: " + response.data.data);
            console.log("page: " + page.value);
            courses.value = response.data.data;
        });
    };

    onBeforeMount(async() => {
        apiKursus(page.value);
    });

    watch(page => {
        apiKursus(page.value);
    })
</script>

<style lang="scss" scoped>

</style>