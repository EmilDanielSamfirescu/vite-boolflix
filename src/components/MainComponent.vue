<script >

import {store} from '../store.js';
import SingleElement from './SingleElement.vue';

export default {
    name: "MainComponent",
    components: {
        SingleElement,
    },
    data (){
        return {
            store
        }
    },
    methods: {
        getFlag(language) {
            if(language == 'it'){
                return 'https://flagicons.lipis.dev/flags/4x3/it.svg';
            } else if(language == 'en') {
                return 'https://flagicons.lipis.dev/flags/4x3/gb.svg';
            }else if(language == 'de') {
                return 'https://flagicons.lipis.dev/flags/4x3/de.svg';
            }else if(language == 'es') {
                return 'https://flagicons.lipis.dev/flags/4x3/es.svg';
            }else if(language == 'fr') {
                return 'https://flagicons.lipis.dev/flags/4x3/fr.svg';
            }else if(language == 'ja') {
                return 'https://flagicons.lipis.dev/flags/4x3/jp.svg';
            }else if(language == 'pt') {
                return 'https://flagicons.lipis.dev/flags/4x3/pt.svg';
            } else {
                return '';
                return 'https://flagicons.lipis.dev/flags/4x3/xx.svg';
            }
        }

    }
};
</script>

<template>
    <main>
        <h2>
            Movies
        </h2>
        <div class="movie-container">
            <div v-for="(movie, i) in store.movies" :key="i">

                <SingleElement :elementData="movie"/>
                
            </div>
        </div>

        <h2>
            Series
        </h2>
        <div class="series-container">
            <div v-for="(singleSeries, i) in store.series" :key="i">

                <SingleElement :elementData="singleSeries"/>
                
            </div>
        </div>
    </main>
</template>

<style lang="scss" scoped>
    main {
        height: 90vh;
        overflow: auto;

        .movie-container, .series-container{
        display: flex;

        div {
            margin: 10px;
        }
    }
    }
</style>