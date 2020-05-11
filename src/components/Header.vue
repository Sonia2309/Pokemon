<template>
  <div>
    <div>
      <div class="hello">
        <div class="left">
          <img
            class="sideimage"
            src="https://upload.wikimedia.org/wikipedia/en/thumb/0/09/AshXYanime.png/220px-AshXYanime.png"
          />
        </div>
        <div>
          <img
            src="..\assets\pokemontitle.jpg"
            style="width: 307px;
    height: 113px;"
          />
        </div>
        <div class="right">
          <img class="sideimage" src="..\assets\teamRocket.png" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.hello {
  display: flex;
  justify-content: space-around;
}
.pokemon {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: var(--text-color);
}
.sideimage {
  height: 200px;
}
</style>
