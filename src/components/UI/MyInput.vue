<template>
   <input :value="modelValue" @input="updateInput" class="input" type="text">
</template>

<script>
export default {
    name: "my-input",
    props: {
        modelValue: [String, Number]
    },
    methods: {
        updateInput(event) {
            this.$emit('update:modelValue', event.target.value)
        }
    }
}
</script>
<style scoped>
        .input {
        widows: 100%;
        border: solid 2px teal;
        padding: 10px 15px;
        margin-top: 20px;
    }
</style>