/* eslint-disable */
<template>
  <div class="splitright rightapp">
    <h1 class="player">{{ player }}</h1>
    <div class="tooltip imgcontainer" v-if="selectedImageB">
      <img class="imgstyle" :src="selectedImageB.img" alt="no img found" />
      <span class="tooltiptext">
        <ul>
          <li>Name: {{ selectedImageB.name }}</li>
          <li>Power:{{ selectedImageB.power }}</li>
        </ul>
      </span>
    </div>
    <button id="myBtn" class="button" href="#" @click="generate()">
      {{ label }}
    </button>
  </div>
</template>

<script>
import pokemon from "../assets/data.json";
import "./styles.css";
export default {
  data() {
    return {
      player: "Player B",
      label: "Hit Me",
      selectedImageB: null
    };
  },
  methods: {
    randomItem(items) {
      return items[Math.floor(Math.random() * items.length)];
    },
    generate() {
      this.selectedImageB = this.randomItem(this.pokemons);
      this.$emit("imageB", this.selectedImageB.speciality);
      this.$emit("powerB", this.selectedImageB.power);

      if (this.label == "Hit Me") {
        document.getElementById("myBtn").disabled = true;
        this.label = "You Cannot Hit Me Again";
      }
      if (document.getElementById("myBtn").innerHTML == "Hit Me") {
        document.getElementById("myBtn").disabled = true;
        document.getElementById("myBtn").innerHTML = "You cannot Hit Me Again";
      }
    }
  },
  computed: {
    pokemons() {
      return pokemon.images.map(item => {
        return item;
      });
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
/* img:hover {
  animation: shake 0.5s;
  animation-iteration-count: infinite;
}

@keyframes shake {
  0% { transform: translate(1px, 1px) rotate(0deg); }
  10% { transform: translate(-1px, -2px) rotate(-1deg); }
  20% { transform: translate(-3px, 0px) rotate(1deg); }
  30% { transform: translate(3px, 2px) rotate(0deg); }
  40% { transform: translate(1px, -1px) rotate(1deg); }
  50% { transform: translate(-1px, 2px) rotate(-1deg); }
  60% { transform: translate(-3px, 1px) rotate(0deg); }
  70% { transform: translate(3px, 1px) rotate(-1deg); }
  80% { transform: translate(-1px, -1px) rotate(1deg); }
  90% { transform: translate(1px, 2px) rotate(0deg); }
  100% { transform: translate(1px, -2px) rotate(-1deg); }
}

.player{
  padding-bottom: 9px;
}
.split {
  height: auto;
  width: 50%;
  display: inline;
  z-index: 1;
  overflow-x: hidden;
  padding-top: 20px;
  float:right;
}
.rightapp {
  right: 0;
}
.imgcontainer{
  height:150px;
  padding-bottom: 2rem;
}
.imgstyle{
  height: 100%;
}

ul {
  list-style-type: none;
  margin: 0;
  padding: 0;
}
/*tool tip//
.tooltiptext {
  visibility: hidden;
  width: 120px;
  background-color:var(--tooltip-color);
  color:var(--white-color);
  border-radius: 6px;
  padding: 5px 0;
  /* Position the tooltip 
  position: absolute;
  z-index: 1;
}

.tooltip:hover .tooltiptext {
  visibility: visible;
}
div{
  clear: both;
} */
</style>
