<template>
    <v-layout>
        <BarTop />

        <v-main>
            <v-container>
                <HeaderMain title="Senarai Kursus TVET" />

                <v-list lines="two">
                    <v-list-subheader inset>Folders</v-list-subheader>

                    <v-list-item v-for="folder in folders" :key="folder.title" :subtitle="folder.subtitle" :title="folder.title">
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
                                @click="dialog = true"
                            ></v-btn>
                        </template>
                    </v-list-item>
                </v-list>
            </v-container>
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
    const dialog = ref(false);
    const folders = [
        {
        subtitle: 'Jan 9, 2014',
        title: 'Photos',
        },
        {
        subtitle: 'Jan 17, 2014',
        title: 'Recipes',
        },
        {
        subtitle: 'Jan 28, 2014',
        title: 'Work',
        },
    ]
</script>

<style lang="scss" scoped>

</style>