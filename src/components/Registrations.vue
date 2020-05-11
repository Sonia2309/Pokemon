<template>
  <div id="registrations">
    <div class="summary">
      <h3>Results</h3>
    </div>
    <div
      class="row"
      v-for="registration in registrations"
      v-bind:key="registration"
    >
      <span>Winner : </span>
      <h4>{{ registration }}</h4>
    </div>
  </div>
</template>

<script>
export default {
  props: ["registrations"]
};
</script>
