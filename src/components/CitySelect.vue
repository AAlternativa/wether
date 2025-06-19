<script setup>
import Input from './Input.vue';
import Button from './Button.vue';
import IconsLocation from '../icons/weather/IconsLocation.vue';
import { inject, ref } from 'vue';
import { cityProvide } from '../constants';



const city = inject(cityProvide)
const inputValue = ref(city.value)
let isEdited = ref(false);


function select() {
    isEdited.value = false;
    city.value = inputValue.value
    // emit('selectCity', city.value)
}
function edit() {
    isEdited.value = true;
}


</script>

<template>
    <div class="city-select">
        <!-- {{ city }} -->
        <!-- {{ isEdited }} -->

        <div v-if="isEdited" class="city-input">
            <Input placeholder="Никольск" v-model="inputValue" @keyup.enter="select" v-focus />

            <Button @click="select()">
                Сохранить
            </Button>
        </div>

        <div v-if="!isEdited">
            <Button @click="edit()">
                <IconsLocation />
                Изменить город
            </Button>
        </div>

    </div>

</template>

<style scoped>
.city-input {
    display: flex;
    gap: 12px;

}

.city-select {
    width: 420px;
}
</style>