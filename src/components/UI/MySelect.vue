<template>
    <select value="modelValue">
        <option disabled value="">Выбрать из списка</option>
        <option
            v-for="option in options"
            :key="option.value"
            :value="option.value"></option>
    </select>
</template>

<script>
export default {
    name: 'my-select',
   props: {
    modelValue: {
        type: String
    }
   }
    
}
</script>

<style>

</style>