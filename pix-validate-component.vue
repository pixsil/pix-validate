<template>
    <div>
        <span class="invalid-feedback d-block" v-show="vueForm.vueErrors.has(field)">
            {{ error }}
        </span>
    </div>
</template>

<script>
export default {

    props: {
        vueForm: {type: Object, required: true},
        field: {type: String, required: true},
        fieldTranslation: String,
        label: String
    },

    components: {
    },

    data() {
        return {
        }
    },

    methods: {
        ucfirst(string) {
            return string.charAt(0).toUpperCase() + string.slice(1);
        }
    },

    mounted() {
    },

    created() {
    },

    computed: {
        error() {
            // get error
            let error = this.vueForm.vueErrors.get(this.field);

            // if we have one
            if (!!error) {
                // if there is given an alternative label
                if (!!this.label) {
                    // override
                    error = this.label
                    // check if we have to use a field translation
                } else if (!!this.fieldTranslation) {
                    let field = field.replaceAll('_', ' ');
                    error = error.replaceAll(field, this.fieldTranslation);
                    error = error.replaceAll(this.ucfirst(field), this.ucfirst(this.fieldTranslation));
                }
            }

            return error;
        }
    }
}
</script>
