<template>
    <v-layout>
        <BarTop />

        <v-main>
            <v-container>
                <v-card title="Carian Institusi TVET" class="mb-3">
                    <v-card-text>
                        <v-text-field v-model="pusat" label="Pusat"></v-text-field>
                    </v-card-text>
                    <v-card-actions>
                        <v-btn color="teal-accent-4" text="Cari" variant="text" @click="apiPusat"></v-btn>
                    </v-card-actions>
                </v-card>

                <v-list>
                    <v-list-group v-for="institute in institutes" :value="institute.pusat">
                        <template v-slot:activator="{ props }">
                            <v-list-item
                            v-bind="props"
                            :title="institute.pusat"
                            ></v-list-item>
                        </template>

                        <ListGroup :pusat="institute.pusat" />
                    </v-list-group>
                </v-list>
                    
                <!-- <v-list lines="two">
                    <v-list-item v-for="institute in institutes" :key="institute.pusat" :title="institute.pusat">
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
                </v-list> -->
            </v-container>
        </v-main>

        <BarBottom menu="1" />
    </v-layout>
</template>

<script setup>
    import axios from "axios";
    const url = "http://mytevt-laravel.test/api/senarai-institusi";
    const institutes = ref([]);
    const pusat = ref();

    const apiPusat = async () => {
        let data = {
            pusat: pusat.value,
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
        apiPusat();
    });
</script>

<style lang="scss" scoped>

</style>