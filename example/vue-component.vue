<template>
    <div>
        <!-- show an overlay on top of the diff when doing the request -->
        <div show-overlay="vueForm.isBusy()" class="loading-overlay">

            <!-- first name field -->
            <div v-if="vueForm.vueErrors.global_message">
                {{ vueForm.vueErrors.global_message }}
            </div>

            <!-- first name field -->
            <label for="first_name">First name:</label><br>
            <input type="text" id="first_name" v-model="vueForm.formData.first_name"><br>

            <!-- Using pix validate for first_name errors -->
            <pix-validate :vue-form="vueForm" field="first_name"></pix-validate>
            
            <!-- last name field-->
            <label for="last_name">Last name:</label><br>
            <input type="text" id="last_name" vueForm.formData.first_name><br><br>
            
            <!-- Using pix validate for last_name errors (with an translation) -->
            <pix-validate :vue-form="vueForm" field="last_name" field-translation="achternaam"></pix-validate>

            <!-- show an message if the form is changed -->
            <div v-if="vueForm.isChanged()">Dont forget to save your changes!</div>

            <!-- first name error-->
            <button @click="submit()" :disabled="!vueForm.isSaveAvailable()">Submit</button>
            <button @click="resetFormdata()" :disabled="!vueForm.isResetAvailable()">Reset</button>
            
        </div>
    </div>
</template>

<script>
export default {
    props: {
    },

    components: {
    },

    data() {
        return {
            vueForm: new VueForm({
                'name': null,
                'last_name': null,
            })
        }
    },

    methods: {
        submit() {
            this.vueForm.post('/user/edit').
                then(response => this.onSuccess())
        },
        onSuccess() {
            // reset the form back to normal
            this.vueForm.resetFormdata()
        }
    },

    mounted() {
    },
}
</script>
