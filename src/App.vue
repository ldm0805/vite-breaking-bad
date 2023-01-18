<script>
import axios from 'axios'
import AppHeader from './components/AppHeader.vue';
import CharacterList from './components/CharacterList.vue';
import { store } from './store.js';
// loaded
export default {
  components: {
    AppHeader,
    CharacterList,
  },
  data() {
    return {
      store
    }
  },
  created() {
    this.getCardsYuGiOh();
  },
  methods: {
    getCardsYuGiOh() {
      axios.get('https://db.ygoprodeck.com/api/v7/archetypes.php').then((response) => {
        store.charactersList = response.data
      })
    },
  },
}
</script>
<template lang="">
  <div class="container-yugi">
    <AppHeader class="p-5" message="Yu-Gi-Oh App"/>

    <main>
      <CharacterList />
    </main>
  </div>
</template>
<style lang="scss">
@use './styles/general.scss' as *;
</style>