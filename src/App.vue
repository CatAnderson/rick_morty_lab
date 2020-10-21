<template>
  <main>
    <h1>Rick and Morty Characters</h1>
    <div class="main-container">
    <character-list v-if='characters.length' :characters='characters'></character-list>
    <character-detail v-if="selectedCharacter" :character='selectedCharacter'></character-detail>
    </div>
  </main>
</template>

<script>
import CharacterList from './components/CharacterList.vue'; 
import CharacterDetail from './components/CharacterDetail.vue';
import { eventBus } from '@/main.js';

export default {
  
  name: 'app',
  data (){
    return {
      characters: [],
      selectedCharacter: null
    };
  },
  mounted () {
    fetch('https://rickandmortyapi.com/api/character/')
    .then(response => response.json())
    .then(characters => this.characters = characters.results);

    eventBus.$on('character-selected', (character) => {
      this.selectedCharacter = character;
    })
  },
components: {
    "character-list": CharacterList,
    'character-detail': CharacterDetail
}
}
</script>

<style>



.main-container {
  font-family: 'Courier New', Courier, monospace;
  display: flex;
  justify-content: space-between;
 
  
}
</style>