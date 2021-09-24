<!-- version 2 -->

<template>
    <div>
        {{ vueForm.vueErrors.has(field) }}
        <span class="invalid-feedback d-block" v-if="vueForm.vueErrors.has(field)">
            {{ getError() }}
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
        },
        getError() {
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
                    let field = this.field.replaceAll('_', ' ');
                    error = error.replaceAll(field, this.fieldTranslation);
                    error = error.replaceAll(this.ucfirst(field), this.ucfirst(this.fieldTranslation));
                }
            }

            return error;
        }
    },

    mounted() {
        if (typeof this.vueForm.vueErrors.fields[this.field] === 'undefined') {
            this.$set(this.vueForm.vueErrors.fields, this.field, null);
        }
    },

    created() {
    },

    computed: {
//        error() {
//
//        }
    }
}
</script>
