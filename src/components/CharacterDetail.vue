<template>
  <article v-if="character">
      <h3> {{ character.name }} </h3>
      <p>Species: {{ character.species }}</p>
      <p>Status: {{ character.status }}</p>
      <img class="char-pic" :src="character.image">

  </article>
</template>

<script>
export default {
    name: 'character-detail',
    props: ['character']
}
</script>

<style lang="css" scoped>
.char-pic {
    height: 300px;
    border-radius: 20px;
    border: 2px solid black;
}


</style>