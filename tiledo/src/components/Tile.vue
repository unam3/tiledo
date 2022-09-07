<script setup>
//defineProps({
//  text: {
//    type: String,
//    required: true
//  }
//})
</script>

<template>
  <div class="tileAndButtonContainer">
        <textarea value="Math.PI aklsd; sa;ldsa lsalasdk laslk ldslsdgk gddd kdflk df ;" />
      <button>Add to-do</button>
  </div>
</template>

<style scoped>

.tile {
  min-height: 10em;
  min-width: 16em;
  border-radius: 0.5em;
  border: 1px solid black;
}

.tileAndButtonContainer textarea {
  display: block;
  min-height: 10em;
  min-width: 16em;
  margin: 0;
  text-align: center;
  border: 2px solid #a94646;
  border-radius: 0.5em;
}

.tileAndButtonContainer button {
    display: block;
    margin: 1em auto;
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

