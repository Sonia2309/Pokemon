<template>
  <div id="app">
    <Header headerLabel="Pokemon" />
    <!--power check logic-->
    <div v-if="imageB !== '' && imageA !== ''">
      <div class="neon" v-if="powerA > powerB">
        <p class="text">{{ playerA }}</p>
        <div v-if="seen">
          <button class="button" @click="addarrayA()">Play Again</button>
        </div>
      </div>
      <div class="neon" v-else-if="powerA < powerB">
        <p class="text">{{ playerB }}</p>
        <div v-if="seen">
          <button class="button" @click="addarrayB()">Play Again</button>
        </div>
      </div>
      <div class="neon" v-else-if="powerA === powerB">
        <p class="text">{{ draw }}</p>
        <div v-if="seen">
          <button class="button" @click="drawgame()">Play Again</button>
        </div>
      </div>
    </div>
    <div>
      <PlayerA
        class="player"
        v-on:imageA="onChildAClick"
        v-on:powerA="onChildCClick"
      />

      <PlayerB
        class="player"
        v-on:imageB="onChildBClick"
        v-on:powerB="onChildDClick"
      />
    </div>
    <app-registrations :registrations="registrations"></app-registrations>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import PlayerA from "./components/leftpane.vue";
import PlayerB from "./components/rightpane.vue";
import Registrations from "./components/Registrations.vue";
import "./components/styles.css";
export default {
  name: "App",
  components: {
    Header,
    PlayerA,
    PlayerB,
    appRegistrations: Registrations
  },
  data() {
    return {
      seen: true,
      imageA: "",
      imageB: "",
      label: "Play",
      registrations: [],
      playerA: "Player A wins",
      playerB: "Player B wins",
      playera: "Player A",
      playerb: "Player B",
      draw: "its a draw"
    };
  },
  computed: {
    unregisteredUsers() {
      return this.users.filter(user => {
        return !user.registered;
      });
    }
  },
  methods: {
    onChildAClick(value) {
      this.imageA = value;
    },
    onChildBClick(value) {
      this.imageB = value;
    },
    onChildCClick(value) {
      this.powerA = value;
    },
    onChildDClick(value) {
      this.powerB = value;
    },
    addarrayA() {
      this.registrations.push(this.playera);
      document.getElementById("myBtn1").disabled = false;
      document.getElementById("myBtn1").innerHTML = "Hit Me";
      document.getElementById("myBtn").disabled = false;
      document.getElementById("myBtn").innerHTML = "Hit Me";
    },
    addarrayB() {
      this.registrations.push(this.playerb);
      document.getElementById("myBtn1").disabled = false;
      document.getElementById("myBtn1").innerHTML = "Hit Me";
      document.getElementById("myBtn").disabled = false;
      document.getElementById("myBtn").innerHTML = "Hit Me";
    },
    drawgame() {
      this.registrations.push(this.draw);
      document.getElementById("myBtn1").disabled = false;
      document.getElementById("myBtn1").innerHTML = "Hit Me";
      document.getElementById("myBtn").disabled = false;
      document.getElementById("myBtn").innerHTML = "Hit Me";
    }
  }
};
</script>
