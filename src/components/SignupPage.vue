<template>
    <div class="container">
        <form action="" class="form">
            <label for="email">Email</label>
            <input type="email" id="email" name="email" v-model="email" :class="{'is-valid': validMail, 'is-invalid': validMail === false, 'form-control': true}">
            <p v-if="validMail === true" class="valid-feedback d-block">You typed a valid mail</p>
            <p v-else-if="validMail === false" class="invalid-feedback d-block">Please type a valid mail</p>
            <label for="password">Password</label>
            <input type="password" id="password" name="password" v-model="password" :class="{'is-valid': validPassword, 'is-invalid': validPassword === false, 'form-control': true}">
            <p v-if="validPassword === true" class="valid-feedback d-block">You typed a valid password</p>
            <p v-else-if="validPassword === false" class="invalid-feedback d-block">Your password is too weak</p>
            <label for="nationality">Nationality</label>
            <select name="nationality" id="nationality" v-model="nationality">
                <option value="en">English</option>
                <option value="de">Deutsch</option>
                <option value="fr">Français</option>
            </select>
        </form>


        <p>{{ message }}</p>

        <p>Your email is {{ email }}</p>


    </div>
</template>

<script setup>
import { ref, computed } from 'vue';

const email = ref("")
const password = ref("")
const nationality = ref("")

const message = computed(() => {
    if (nationality.value === "en") {
        return "Hello"
    } else if (nationality.value === "de") {
        return "Hallo"
    } else if (nationality.value === "fr") {
        return "Bonjour"
    }
})

const validMail = computed(() => {
    const pattern = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
    return pattern.test(email.value);
});


const validPassword = computed(() => {
    const pattern = /^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[!@#$%^&*])[A-Za-z\d!@#$%^&*]{8,}$/
    return pattern.test(password.value)
})

</script>

<style scoped>
.container {
    .form {
        max-width: 30vw;
        display: flex;
        flex-direction: column;
        gap: 1vh;
    }

}




</style>