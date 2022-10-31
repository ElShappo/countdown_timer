<template>
<div v-if="showTimer" class="timer">
    <div><span class="name">{{days}}</span><span class="text-name"><div>days</div></span></div>
    <div><span class="name">{{hours}}</span><span class="text-name"><div>hours</div></span></div>
    <div><span class="name">{{minutes}}</span><span class="text-name"><div>minutes</div></span></div>
    <div><span class="name">{{seconds}}</span><span class="text-name"><div>seconds</div></span></div>
</div>
<div  id="endOfCountdown" v-if="isEndOfCountdown">End of countdown!</div>
</template>

<script>
export default {
    name: "TimerPage",

    data() {
        return {
            days: 0,
            hours: 0,
            minutes: 0,
            seconds: 0,

            showTimer: false,
            isEndOfCountdown: false,
        }
    },

    props: {
        countDownDate: Date,
    },

    methods: {
        startCountdown() {
            let timer = setInterval( () => {
            let now = new Date().getTime();
            var difference = this.countDownDate.getTime() - now;

            if (difference > 0) {
                this.days = Math.floor(difference / (1000 * 60 * 60 * 24));
                this.hours = Math.floor((difference % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
                this.minutes = Math.floor((difference % (1000 * 60 * 60)) / (1000 * 60));
                this.seconds = Math.floor((difference % (1000 * 60)) / 1000);
            } else {
                this.isEndOfCountdown = true;
                clearInterval(timer);
            }
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
    column-gap: 5vh;
}

.name {
    font-weight: bold;
    font-size: 4vw;
}

#endOfCountdown {
    padding-top: 2vh;
}

</style>