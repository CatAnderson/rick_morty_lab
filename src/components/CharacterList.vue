<template lang="html">
  <div>
    <label for="character_select">Select Character</label>
    <select name="" id="character_select" v-on:change="handleSelect" v-model="selectCharacter">
    <option disabled value="">Select Character</option>
    <option v-for="(character, index) in characters" :key="index" :value="character">{{ character.name }}</option>
    </select>

      <!-- <ul>
      <list-item v-for="(character, index) in characters" :character="character" :key="index">{{ character.name }}</list-item>
      </ul> -->
    </div>
</template>

<script>
import {eventBus} from '@/main.js';
// import ListItem from './ListItem.vue';

export default {
    name: "character-list",
    props: ["characters"],

    data(){
        return{
            selectCharacter: {}
    }
    },
    // components: {
    //     "list-item": ListItem
    // },

    methods: {
        handleSelect: function(){
            eventBus.$emit('character-selected', this.selectCharacter);
        }
    }
}
</script>

<style lang="css" scoped>

</style>