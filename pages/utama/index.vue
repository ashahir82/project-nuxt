<template>
    <v-layout>
        <BarTop />

        <v-main>
            <v-container>
                <HeaderMain title="Selamat Datang ke myTVET" />
                <p>Penerangan berkaitan myTVET</p>

                <v-divider class="my-3"></v-divider>
                
                <v-row>
                    <v-col cols="12" lg="3" sm="6">
                        <CardNormal title="Institusi TVET" subtitle="Senarai Institusi TVET di Malaysia" url="institusi" />
                    </v-col>
                    <v-col cols="12" lg="3" sm="6">
                        <CardNormal title="Kursus TVET" subtitle="Senarai Kursus TVET di Malaysia" url="kursus" />
                    </v-col>
                </v-row>
            </v-container>
        </v-main>

        <BarBottom menu="0" />
    </v-layout>
</template>

<script setup>
    
</script>

<style lang="scss" scoped>

</style>