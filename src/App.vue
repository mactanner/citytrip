<script setup lang="ts"></script>

<template>
  <header>
    <h1>City Trip 2024</h1>
    <div class="teaser">Bald ist es soweit!</div>
  </header>

  <body>
    <CountdownTimer />
    <div>Ihr fragt euch bestimmt: Wo geht's denn dieses Jahr hin?</div>
    <br />
    <div>
      Und weil Vorfreude bekanntlich die schönste Freude ist, gibt es hier in den nächsten Tagen ein
      paar Hinweise dazu. Auf geht's:
    </div>
    <br />
    <ul>
      <li>Wir verlassen die Schweiz.</li>
      <li>Man spricht dort nicht Deutsch.</li>
    </ul>
  </body>
</template>

<script>
import CountdownTimer from './components/CountdownTimer.vue'

export default {
  components: {
    CountdownTimer
  }
}
</script>

<style scoped>
h1 {
  background: -webkit-linear-gradient(315deg, #42d392, #647eff);
  background-clip: text;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  font-family: 'Roboto', sans-serif;
  font-size: 80px;
  font-weight: 900;
  letter-spacing: -1px;
}
.teaser {
  font-weight: 500;
  font-size: 20px;
}
body {
  max-width: 500px;
  font-family: 'Roboto', sans-serif;
}
li::marker {
  color: #42d392;
}
ul {
  padding-left: 1em;
}
@media (max-width: 800px) {
  h1 {
    font-size: 60px;
    letter-spacing: -1px;
  }
}
@media (max-width: 500px) {
  h1 {
    font-size: 44px;
    letter-spacing: -1px;
  }
}
</style>
