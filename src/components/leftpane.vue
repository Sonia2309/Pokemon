<template>
  <div class="splitleft leftapp">
    <h1 class="player">{{ player }}</h1>
    <div class="imgcontainer tooltip" v-if="selectedImageA">
      <img class="imgstyle" :src="selectedImageA.img" alt="no img found" />
      <span class="tooltiptext">
        <ul>
          <li>Name: {{ selectedImageA.name }}</li>
          <li>Power: {{ selectedImageA.power }}</li>
        </ul>
      </span>
    </div>
    <button id="myBtn1" class="button" href="#" @click="generate()">
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
      player: "Player A",
      label: "Hit Me",
      selectedImageA: null
    };
  },
  methods: {
    randomItem(items) {
      return items[Math.floor(Math.random() * items.length)];
    },
    generate() {
      console.log(this.pokemons);
      this.selectedImageA = this.randomItem(this.pokemons);
      this.$emit("imageA", this.selectedImageA.speciality);
      this.$emit("powerA", this.selectedImageA.power);

      if (this.label == "Hit Me") {
        document.getElementById("myBtn1").disabled = true;
        this.label = "You cannot Hit Me Again";
      }
      if (document.getElementById("myBtn1").innerHTML == "Hit Me") {
        document.getElementById("myBtn1").disabled = true;
        document.getElementById("myBtn1").innerHTML = "You cannot Hit Me Again";
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
