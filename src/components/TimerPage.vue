<template>
<div v-if="showTimer" class="timer">
    <div> <span class="name">{{days}}</span> <span class="text-name">days</span> </div>
    <div> <span class="name">{{hours}}</span> <span class="text-name">hours</span> </div>
    <div> <span class="name">{{minutes}}</span> <span class="text-name">minutes</span> </div>
    <div> <span class="name">{{seconds}}</span> <span class="text-name">seconds</span> </div>
</div>
</template>

<script>
export default {
    name: "TimerPage",

    data() {
        return {
            days: null,
            hours: null,
            minutes: null,
            seconds: null,

            showTimer: false,
        }
    },

    props: {
        countDownDate: Date,
    },

    methods: {
        startCountdown() {
            setInterval( () => {
            let now = new Date().getTime();
            let difference = this.countDownDate.getTime() - now;

            this.days = Math.floor(difference / (1000 * 60 * 60 * 24));
            this.hours = Math.floor((difference % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
            this.minutes = Math.floor((difference % (1000 * 60 * 60)) / (1000 * 60));
            this.seconds = Math.floor((difference % (1000 * 60)) / 1000);

            this.showTimer = true;
            }, 1000);
            
        }
    },

    mounted() {
        this.startCountdown();
    },
}
</script>

<style>

.timer {
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    column-gap: 1vh;
}

.name {
    font-weight: bold;
    font-size: x-large;
}

</style>