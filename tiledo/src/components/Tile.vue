<script setup>

defineProps({
  todoText: String
})

</script>

<template>
  <div class="tile">
      <!--
      <textarea :value="todoText" />
      -->
      {{ todoText }}
  </div>
</template>

<style scoped>

/*
.tile {
  padding: 3em;
  min-height: 10em;
  min-width: 16em;
  border-radius: 0.5em;
  border: 1px solid black;
}

.tileAndButtonContainer {
  padding: 2em;
}

.tileAndButtonContainer textarea {
*/
.tile {
  display: flex;
  align-items: center;
  justify-content: center;
  align-content: center;
  min-height: 10em;
  min-width: 16em;
  margin: 2em;
  padding: 2em;
  border: 2px solid #a94646;
  border-radius: 0.5em;
}

.tile:hover {
  background-color: #eee8aa;
  border-color: #808080;
}

.pluh {
  background-color: #eee8aa;
  border-color: #808080;
}

</style>

