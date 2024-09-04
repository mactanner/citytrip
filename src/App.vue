<script setup lang="ts"></script>

<template>
  <header>
    <div style="text-align: center" v-if="isDestinationFound">
      <h1>Montpellier</h1>
      <div class="teaser">Wir kommen!</div>
    </div>
    <div style="text-align: center" v-else>
      <h1>City Trip 2024</h1>
      <p class="teaser">Bald ist es soweit!</p>
    </div>
  </header>

  <body>
    <CountdownTimer />

    <div v-if="isDestinationFound">
      <p>
        Die pulsierende Stadt im sonnigen Süden Frankreichs erwartet uns mit ihrer charmanten
        Altstadt, lebhaften Atmosphäre und der Nähe zum funkelnden Mittelmeer! 🤩
      </p>
      <h2>Reise</h2>
      <h3>Treffpunkt</h3>
      <p>
        Freitag, 6. September 08:30 Uhr bei Alain.<br />Mac fährt mit dem Auto an den Flughafen
        Basel. Am Sonntag wird's etwas spät mit der Rückreise. Daher sind wir mit dem Auto wohl am
        besten bedient.
      </p>
      <h3>Hinflug: Basel - Montpellier</h3>
      <p>Freitag, 6. September</p>
      <p>🛫 11:55</p>
      <p>🛬 13:10</p>
      <h3>Rückflug: Montpellier - Basel</h3>
      <p>Sonntag, 8. September</p>
      <p>🛫 21:45</p>
      <p>🛬 23:00</p>
      <br />
      <div>
        <b>Wichtig:</b> Ich habe nur ein kleines Handgepäck pro Person gebucht (45 x 36 x 20 cm).
        Wenn euch das zu knapp ist, bitte bei mir melden.
      </div>
      <div>
        <a href="https://www.easyjet.com/de/hilfe/gepack/handgepack" target="_blank"
          >Weitere Infos</a
        >
      </div>
      <h2>Unterkunft</h2>
      <div>JOST Hotel Montpellier Centre St Roch</div>
      <div>
        <a href="https://www.jost-hotel-montpellier.com/" target="_blank">Hotel Webseite</a>
      </div>
      <h2>Programm</h2>
      <h3>Freitag, 6. September</h3>
      <ul>
        <li>Anreisen & Einpuffen</li>
        <li>Savoir-vivre und Laissez-faire in Montpellier</li>
        <li>Nachtessen im Angus & Bacchus</li>
      </ul>
      <h3>Samstag, 7. September</h3>
      <ul>
        <li>Petit-déjeuner</li>
        <li>Savoir-vivre und Laissez-faire in Montpellier</li>
        <li>Rugby Spiel: Montpellier Hérault Rugby - Lyon Olympique Universitaire</li>
      </ul>
      <h3>Sonntag, 8. September</h3>
      <ul>
        <li>Petit-déjeuner</li>
        <li>Savoir-vivre und Laissez-faire in Pérols am Meer</li>
        <li>Heimreise</li>
      </ul>
      <br />
      <p></p>
    </div>
    <div v-else>
      <div>Ihr fragt euch bestimmt: Wo geht's denn dieses Jahr hin?</div>
      <br />
      <div>
        Und weil Vorfreude bekanntlich die schönste Freude ist, gibt es hier in den nächsten Tagen
        ein paar Hinweise dazu. Auf geht's:
      </div>
      <br />
      <ul>
        <li>Wir verlassen die Schweiz.</li>
        <li>Man spricht dort nicht Deutsch.</li>
        <li>Die Stadt liegt an einem Gewässer.</li>
        <li>Es handelt sich um eine Studentenstadt.</li>
        <li>Unser Ziel liegt südlich von Luzern.</li>
        <li>In der Region gibt es guten Wein. 🍷</li>
        <li>Die Stadt hat mehr als 200'000 Einwohner.</li>
        <li>Die Altstadt ist ein Labyrinth aus engen Gassen und versteckten Plätzen.</li>
      </ul>
      <br />
      <div>Nun bist du dran: Wohin gehen wir?</div>
      <br />
      <form @submit.prevent="checkCity">
        <input class="city-input" type="text" id="city" v-model="cityName" placeholder="City" />
        <button type="submit" class="submit-button">Check</button>
      </form>
      <br />
      <div v-if="wrongInput">
        <p>Nönönö. Probier's nochmals.</p>
      </div>
    </div>
  </body>
</template>

<script>
import CountdownTimer from './components/CountdownTimer.vue'

export default {
  components: {
    CountdownTimer
  },
  data() {
    return {
      cityName: '',
      isDestinationFound: true,
      wrongInput: false
    }
  },
  methods: {
    checkCity() {
      if (btoa(this.cityName.trim().toLowerCase()) === 'bW9udHBlbGxpZXI=') {
        this.isDestinationFound = true
        this.wrongInput = false

        // Scroll to the top of the page
        window.scrollTo({
          top: 0,
          behavior: 'smooth' // Optional: adds a smooth scrolling effect
        })
      } else {
        this.isDestinationFound = false
        this.wrongInput = true
      }
    }
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
h2 {
  margin-top: 1em;
  font-weight: 600;
}
h3 {
  margin-top: 0.8em;
  font-weight: 600;
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
.city-input {
  font-size: 24px; /* Large font size */
  padding: 10px 15px;
  border-image-source: -webkit-linear-gradient(315deg, #42d392, #647eff);
  border-image-slice: 1;
  border-radius: 4px 0 0 4px; /* Rounded corners on the left side */
  outline: none;
  box-sizing: border-box; /* Ensures padding doesn't affect width */
  background: #e1e1e1;
}
.submit-button {
  font-size: 24px; /* Match the input font size */
  padding: 10px 20px;
  border: 2px solid #333;
  border-left: none; /* Remove the border between input and button */
  border-radius: 0 4px 4px 0; /* Rounded corners on the right side */
  background-color: #333;
  color: white;
  cursor: pointer;
  outline: none;
}

input::placeholder {
  color: grey;
  opacity: 0.8;
}

.submit-button:hover {
  background-color: #555; /* Change color on hover */
}

/* Ensures input and button are on the same height */
form {
  display: flex;
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
  .city-input {
    font-size: 16px;
    padding: 10px 10px;
  }
  .submit-button {
    font-size: 16px;
    padding: 10px 10px;
  }
}
</style>
