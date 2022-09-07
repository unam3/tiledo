<script setup>
//defineProps({
//  text: {
//    type: String,
//    required: true
//  }
//})
</script>

<template>
  <div class="tile">
        <input type="text" v-bind:value="Math.PI" />
        <button>{{ Math.PI }}</button>
  </div>
</template>

<style scoped>

.tile {
  min-height: 10em;
  min-width: 16em;
  border: 2px solid #a94646;
  border-radius: 0.5em;
  text-align: center;
}

.greetings h3 {
  text-align: center;
}

@media (min-width: 1024px) {
  .greetings h3 {
    text-align: left;
  }
}
</style>

