<template>
  <div class="container bg-success-subtle shadow w-75 p-5">
    <h1 class="fw-bold mb-5">Countdown in:</h1>
    <div class="row">
        <div class="col-12 col-md-3 day">
            <p class="number fw-bold display-2 mb-0">{{ days }}</p>
            <p class="fs-4 fw-bold">Days</p>
        </div>
        <div class="col-12 col-md-3 hour">
            <p class="number fw-bold display-2 mb-0">{{ hours }}</p>
            <p class="fs-4 fw-bold">Hours</p>
        </div>
        <div class="col-12 col-md-3 minute">
            <p class="number fw-bold display-2 mb-0">{{ minutes }}</p>
            <p class="fs-4 fw-bold">Minutes</p>
        </div>
        <div class="col-12 col-md-3 second">
            <p class="number fw-bold display-2 mb-0">{{ seconds }}</p>
            <p class="fs-4 fw-bold">Seconds</p>
        </div>
    </div>
  </div>
  <div class="container p-5">
    <label for="time-countdown" class="fw-bold mb-3 display-6">Choose time need to count down:</label> <br>
    <input type="datetime-local" id="time-countdown" v-model="timeCountdown" step="1" class="text-dark fw-bold p-3 fs-4 bg-light bg-opacity-25 shadow">
  </div>
</template>

<script>
export default {
    name: 'Countdown',
    data() {
        return {
            timeCountdown: '2024-01-01T00:00:00',
            days: null,
            hours: null,
            minutes: null,
            seconds: null,
            futureTime: null,
            currentTime: null,
            diff: null,
        }
    },
    methods: {
        calculateDiff() {
            this.futureTime = new Date(this.timeCountdown).getTime();
            this.currentTime = new Date().getTime();
            this.diff = (this.futureTime - this.currentTime) / 1000;
            this.days = Math.floor(this.diff / 86400);
            this.hours = Math.floor((this.diff - 86400 * this.days) / 3600);
            this.minutes = Math.floor((this.diff - 86400 * this.days - 3600 * this.hours) / 60);
            this.seconds = Math.floor(this.diff - 86400 * this.days - 3600 * this.hours - 60 * this.minutes);
        }
    },
    mounted() {
        setInterval(this.calculateDiff, 1000);
    },
    updated() {
        setInterval(this.calculateDiff, 1000);
    }
}
</script>