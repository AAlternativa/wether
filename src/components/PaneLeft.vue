<script setup>
import { computed, inject } from 'vue'
import { cityProvide } from '../constants'
import IconsLocation from '../icons/weather/IconsLocation.vue'
import IconSun from '../icons/weather/IconSun.vue'
import IconsRain from '../icons/weather/IconsRain.vue'
import IconsCloud from '../icons/weather/IconsCloud.vue'
const { dayData } = defineProps({
    dayData: Object,
})

const city = inject(cityProvide)


const day = computed(() => {
    return new Date(dayData.date).toLocaleDateString('ru-RU', { weekday: "long" })
})

const date = computed(() => {
    return new Date(dayData.date).toLocaleDateString('ru-RU', {
        day: 'numeric',
        month: "long",
        year: 'numeric'
    })
})


const weatherCode = computed(() => {
    return dayData.day.condition.code;
})
</script>




<template>
    <div class="paneLeft">
        <div>
            <div class="day">
                {{ day }}
            </div>
            <div class="date">
                {{ date }}
            </div>
            <div class="city">
                <IconsLocation />
                {{ city }}
            </div>
        </div>

        <div>
            <div class="wetherIcon">
                <IconSun v-if="weatherCode <= 1003" size="95" />
                <IconsRain v-if="weatherCode > 1003 && weatherCode < 1063" size="95" />
                <IconsCloud v-if="weatherCode >= 1063" size="95" />
            </div>
            <div class="temp">
                {{ dayData.day.avgtemp_c }} °C
            </div>
            <div class="condition">
                {{ dayData.day.condition.text }}
            </div>
        </div>
    </div>

</template>

<style scoped>
.paneLeft {
    display: flex;
    flex-direction: column;
    padding: 48px 32px;
    justify-content: space-between;
    height: 100%;
}

.day {
    font-size: 37px;
    font-weight: 700;
    text-transform: capitalize;
    margin-bottom: 16px;
}

.wetherIcon {
    margin: 25px;
}

.date {
    font-size: 22px;
    font-weight: 500;
    margin-bottom: 10px;
}

.city {
    display: flex;
    gap: 8px;
    align-items: center;
}

.temp {
    font-size: 50px;
    font-weight: 700;
    margin-bottom: 9px;
}

.condition {
    font-size: 37px;
    font-weight: 500;
}
</style>