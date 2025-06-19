<!-- eslint-disable vue/multi-word-component-names -->
<script setup>
const model = defineModel({ type: String, required: true });
import { onUpdated } from 'vue';

onUpdated(() => {
    console.log('input updated');
});

</script>

<template>
    <input class="input" v-model="model">
</template>

<style scoped>
.input {
    color: var(--color-primary);
    width: 260px;
    height: 53px;
    border-radius: 10px;
    border: none;
    padding: 15px 20px;
    font-size: 18px;
    background: var(--color-bg-card);
    box-shadow: 1px 2px 4px 0px var(--color-bg-main);

}

.input::placeholder {
    color: var(--color-text-placeholder);
}
</style>