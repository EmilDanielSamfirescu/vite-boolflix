<script >
import {store} from '../store.js';
export default {
    name: "MainComponent",
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
        <ul>
            <li v-for="(movie, i) in store.movies" :key="i">
                <ol>
                    <li>
                        {{ movie.title }}
                    </li>

                    <li>
                        {{ movie.original_title }}
                    </li>

                    <li>
                        <img :src="getFlag(movie.original_language)" :alt="movie.original_language.toUpperCase()">
                    </li>

                    <li>
                        {{ movie.vote_average }}
                    </li>

                </ol>
            </li>
        </ul>

        <h2>
            Series
        </h2>
        <ul>
            <li v-for="(singleSeries, i) in store.series" :key="i">
                <ol>
                    <li>
                        {{ singleSeries.name }}
                    </li>

                    <li>
                        {{ singleSeries.original_name }}
                    </li>

                    <li>
                        <img :src="getFlag(singleSeries.original_language)" :alt="singleSeries.original_language.toUpperCase()">
                    </li>

                    <li>
                        {{ singleSeries.vote_average }}
                    </li>

                </ol>
            </li>
        </ul>
    </main>
</template>

<style lang="scss" scoped>
    img {
        width: 30px;
    }
</style>