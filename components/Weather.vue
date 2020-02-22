<template>
    <div>
        <h2>Current Weather</h2>
        <form @submit.prevent="getWeather">
            <input type="text" v-model="weatherInput" />
            <div v-text="description"></div>
            <div v-if="temp" class="Temp">
                <div class="TempEl" :style="{ width: temp + '%' }">{{temp}}℉</div>
            </div>
        </form>
    </div>
</template>

<script>
export default {
    // make ajax call on enter
    data() {
        return {
            weatherInput: '',
            temp: '',
            description: ''
        }
    },
    methods: {
        getWeather() {
            console.log(`get weather: ${this.weatherInput}`)
            fetch(`http://api.openweathermap.org/data/2.5/weather?q=${this.weatherInput}&units=imperial&appid=eb0a4ddf6567cd991f2f7b64ad53d8c7`)
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
        background: lightgray;
    }
    .TempEl {
        width: 0;
        background-color: gray;
        transition: width ease 1s;
        text-align: right;
    }
</style>