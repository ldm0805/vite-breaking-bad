<script>
import CharacterCard from './CharacterCard.vue';
import AppCardToGiOh from './AppCardToGiOh.vue';
import AppSelect from './AppSelect.vue';
import ResultMessage from './ResultMessage.vue';

import { store } from '../store.js';
import axios from 'axios';


export default {
    name: 'CharacterList',
    components: {
        CharacterCard,
        AppCardToGiOh,
        AppSelect,
        ResultMessage
    },
    data() {
        return {
            store,
        }
    },
    methods: {
        select_archetype(value) {
            axios.get(`https://db.ygoprodeck.com/api/v7/cardinfo.php?archetype=${value}`).then((response) => {
                store.cards = response.data.data;
                store.loading = false;
            })
        }
    }
}
</script>
<template lang="">
    <div class="container_select">
        <div class="found">
            <AppSelect :archetype="store.charactersList" @selection="select_archetype" />
           <ResultMessage/>
        </div>
        <div class="loading" v-if="store.loading">
            <h2>Sto credendo nel cuore delle carte</h2>
            <svg viewBox="0 0 50 50">
                <circle cx="25" cy="25" r="20" />
            </svg>
        </div>
        <div v-else> 
            <CharacterCard/>
     </div>
    </div>
</template>
<style lang="scss" scoped>
@use '../styles/partials/variables' as *;
@use '../styles/partials/mixins' as *;

.container_select {
    background-color: white;
    margin-bottom: 2em;

    .container_card {
        @include between;
    }

    .found {
        padding: 1em 2em;
        background-color: rgb(62, 62, 62);
        @include upbold;
        color: white;
    }

    .loading {
        display: flex;
        justify-content: center;
        align-items: center;
        gap: 2em;

        svg {
            width: 4em;
            height: 4em;
            animation: spin 1s linear infinite;

            @keyframes spin {
                100% {
                    rotate: 360deg;

                }
            }

            @keyframes dash {
                0% {
                    stroke-dasharray: 1, 150;
                    stroke-dasharray: 0;
                }

                50% {
                    stroke-dasharray: 90, 150;
                    stroke-dasharray: -35;
                }

                100% {
                    stroke-dasharray: 90, 150;
                    stroke-dasharray: -124;
                }
            }
        }

        circle {
            fill: none;
            stroke: #000000;
            stroke-width: 3px;
            stroke-linecap: round;
            animation: dash 3s ease-in-out infinite
        }
    }
}
</style>

<!-- import * as utils from ".named-export.js" -->