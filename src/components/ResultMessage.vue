
<script>
import { store } from '../store.js';
export default {
    name: 'ResultMessage',
    data() {
        return {
            store
        }
    },
    computed: {
        numberResults() {
            return store.cards.length
        }
    }
}
</script>
<template lang="">
    <div>
        <h2>
            Trovati {{numberResults}} risultati
        </h2>
    </div>
</template>
<style lang="scss" scoped>

</style>