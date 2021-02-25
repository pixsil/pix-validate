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
        vueForm: Object,
        field: String,
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
                }
            }

            return error;
        }
    }
}
</script>
