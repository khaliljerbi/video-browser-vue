<template>
<div class="w-100">
    <v-text-field label="Search videos here" @input="onTermChange"></v-text-field>
</div>
</template>

<script>
export default {
    name: "SearchBar",
    methods: {
        onTermChange(text) {
            this.$emit("term-change", text);
        },
    },
};
</script>

<style scoped>
.w-100 {
    width: 100%;
}
</style>
