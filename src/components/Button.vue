<!-- eslint-disable vue/multi-word-component-names -->
// eslint-disable-next-line vue/multi-word-component-names
<script setup>

</script>

<template>
    <button class="button">
        <div>
            <slot name="icon"></slot>
            <slot name="text"></slot>
        </div>
        <slot />
    </button>
</template>

<style scoped>
.button {
    border: none;
    border-radius: 10px;
    background: var(--gradient);
    padding: 14px;
    font-family: var(--font);
    font-size: 20px;
    font-weight: 600px;
    color: var(--primary);
    cursor: pointer;
    display: flex;
    height: 53px;
    width: 100%;
    gap: 9px;
    align-items: center;
    justify-content: center;
}

.button:hover {
    background: var(--gradient-inverted);
}
</style>