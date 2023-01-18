<script>
import AppCardToGiOh from './AppCardToGiOh.vue';
import { store } from '../store.js';
export default {
    name: 'CharacterCard',
    components: {
        AppCardToGiOh,
    },
    data() {
        return {
            store,
        }
    },
}
</script>
<template lang="">
    <div class="character d-flex justify-content-center">
        <div class="container_card d-flex flex-wrap justify-content-between">
            <div v-for="(value, index) in store.cards" :key="index">
                <AppCardToGiOh :url="value.card_images[0].image_url" :title="value.name" :type="value.archetype" />
            </div>
        </div>
    </div>




</template>
<style lang="scss" scoped>
@use '../styles/partials/variables' as *;
@use '../styles/partials/mixins' as *;
</style>