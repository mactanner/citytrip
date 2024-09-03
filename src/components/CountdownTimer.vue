<template>
  <div>
    <p>{{ countdown }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      countDownDate: new Date('September 6, 2024 08:00:00').getTime(),
      countdown: ''
    }
  },
  mounted() {
    this.startCountdown()
  },
  methods: {
    startCountdown() {
      this.updateCountdown()
      this.interval = setInterval(this.updateCountdown, 1000)
    },
    updateCountdown() {
      const now = new Date().getTime()
      const distance = this.countDownDate - now

      if (distance < 0) {
        clearInterval(this.interval)
        this.countdown = '🚀'
        return
      }

      const days = Math.floor(distance / (1000 * 60 * 60 * 24))
      const hours = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60))
      const minutes = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60))
      const seconds = Math.floor((distance % (1000 * 60)) / 1000)

      this.countdown = `${days}d ${hours}h ${minutes}min ${seconds}s`
    }
  },
  beforeUnmount() {
    clearInterval(this.interval)
  }
}
</script>

<style scoped>
div {
  margin-top: 2em;
  margin-bottom: 2em;
}
p {
  font-family: 'Roboto', sans-serif;
  font-size: xx-large;
  font-weight: 600;
  text-align: center;
}
</style>
