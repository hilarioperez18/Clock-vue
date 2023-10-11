<script>
export default {

    data() {
        return { //Diego subelo a git y pasa el repo
            hours: '00',
            minutes: '00',
            seconds: '00',
            color: "",
        };
    },
    mounted() {
        setInterval(() => (this.getRandomColor(), this.getTime()), 1000)
    },
    methods: {
        getTime() {
            const now = new Date();
            this.hours = now.getHours().toString().padStart(2, '0');
            this.minutes = now.getMinutes().toString().padStart(2, '0');
            this.seconds = now.getSeconds().toString().padStart(2, '0');
        },
        getRandomColor() {

            const r = Math.floor(Math.random() * 256);
            const g = Math.floor(Math.random() * 256);
            const b = Math.floor(Math.random() * 256);


            this.color = `#${r.toString(16)}${g.toString(16)}${b.toString(16)}`;
        },

    },
    computed: {
        am_pm() {
            return this.hours < 12 ? 'AM' : 'PM'
        }
    }
}

</script>

<template>
    <div class="clock-container">
        <div class="inner">

            <div class="hours">{{ hours }}</div>
            <div class="dots">:</div>
            <div class="minutes">{{ minutes }}</div>
            <div class="dots">:</div>
            <div class="seconds">{{ seconds }}</div>
            <div class="am_pm">{{ am_pm }}</div>
        </div>
    </div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@400;600&display=swap');

.clock-container {
    width: 380px;
    height: 100px;
    background-color: aqua;
    display: flex;
    justify-content: center;
    align-items: center;
}

.inner {
    background-color: black;
    display: flex;
    width: 95%;
    height: 93%;

}

.inner * {
    color: v-bind(color);
    text-shadow:
        0 0 10px v-bind(color),
        0 0 20px v-bind(color),
        0 0 40px v-bind(color),
        0 0 80px v-bind(color),
        0 0 90px v-bind(color),
        0 0 100px v-bind(color);
    font-family: 'Orbitron', sans-serif;
    font-size: 3rem;

}


body {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    margin: 0;
    background-color: #f0f0f0;
}

.clock-container {
    background-color: #333;
    color: white;
    border: 2px solid #555;
    border-radius: 10px;
    display: flex;
    justify-content: center;
    align-items: center;
    font-family: Arial, sans-serif;
    font-size: 24px;
    font-weight: bold;
}

.inner {
    display: flex;
    align-items: center;
    justify-content: center;
}

.dots {
    margin: 0 5px;
}

.hours,
.minutes,
.seconds {
    padding: 5px;
}

.am_pm {
    font-size: 18px;
    margin-left: 20px;
}
</style>
