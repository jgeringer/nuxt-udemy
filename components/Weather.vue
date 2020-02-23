<template>
    <section>
        <h1 class="intro mb-4 mt-5">Current Weather</h1>
        <form @submit.prevent="getWeather">
            <input type="text" v-model="weatherInput" placeholder="Enter Location..." />
            <div v-if="temp" class="Temp">
                <div class="TempEl" :style="{ width: temp + '%' }">{{temp}}℉</div>
                <span v-text="description"></span>
            </div>
        </form>
    </section>
</template>

<script>
export default {
    // make ajax call on enter
    data() {
        return {
            weatherInput: '',
            temp: 0,
            description: ''
        }
    },
    methods: {
        getWeather() {
            console.log(`get weather: ${this.weatherInput}`)
            fetch(`//api.openweathermap.org/data/2.5/weather?q=${this.weatherInput}&units=imperial&appid=eb0a4ddf6567cd991f2f7b64ad53d8c7`)
                .then((response) => {
                    return response.json()
                })
                .then((result) => {
                    console.log(result)
                    this.temp = result.main.temp
                    this.description = result.weather[0].description
                })
        }
    }
}
</script>

<style scoped>
    .Temp {
        width: 100%;
        display: flex;
        align-items: center;
        margin-top: 1rem;
        border-radius: 8px;
        overflow: hidden;
        font-size: 1.4rem;
        background: linear-gradient(117deg, rgba(0,112,255,1) 0%, rgba(221,135,36,1) 45%, rgba(191,19,19,1) 100%);
    }
    .TempEl {
        width: 0;
        background-color: gray;
        transition: width ease 1s;
        text-align: right;
        mix-blend-mode: screen;
        padding: 1rem;
        font-weight: bold;
        border-right: white 1px solid;
    }
    span {
        padding: 1rem;
        color: #fff;
    }
    input {
        width: 100%;
        border-radius: 6px;
        padding: 1rem;
        font-size: 1.4rem;
        border: 1px solid gray;
    }
    section {
        margin-bottom: 3rem;
    }
</style>