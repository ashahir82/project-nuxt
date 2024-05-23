<template>
    <div class="ma-3">
        <v-sheet>
            <v-form @submit.prevent="onSubmit">
                <v-text-field v-model="email" :rules="ruleEmail" label="Email"></v-text-field>
                <v-text-field type="password" v-model="password" label="Password"></v-text-field>
                <div align="center">
                    <v-btn class="mt-2" type="submit">Login</v-btn>
                </div>
            </v-form>
        </v-sheet>
    </div>
</template>

<script setup>
    const email = ref("");
    const password = ref("");
    const sah = ref(false);
    const ruleEmail = [
    (value) => {
        if (value) return true;
        return "Sila Masukkan Email";
    },
    (value) => {
        if (/.+@.+\..+/.test(value)) {
        sah.value = true;
        return true;
        }
        return "Sila Masukkan Email Yang Sah";
    },
    ];

    import axios from "axios";
    const router = useRouter();
    const onSubmit = async () => {
        if (sah.value === true) {
            await axios
            .get("http://mytevt-laravel.test/sanctum/csrf-cookie")
            .then((response) => {
                let url ="http://mytevt-laravel.test/api/login";
                let data = {
                    email: email.value,
                    password: password.value, 
                };
                const config = {
                    headers: {
                        Accept: "application/json",
                    },
                };
                axios.post(url, data, config).then((response) => {
                    console.log(response.data);
                    if(response.data.success === true) {
                        localStorage.setItem("token", response.data.data.token)
                        router.replace("/");
                    } else {
                        console.log(response.data.message);
                    }
                });
            });
        }
    };
</script>

<style scoped>
</style>