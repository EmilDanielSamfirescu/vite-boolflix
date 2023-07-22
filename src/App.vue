<script >
import HeaderComponent from './components/HeaderComponent.vue';
import MainComponent from './components/MainComponent.vue';
import FooterComponent from './components/FooterComponent.vue';
import axios from 'axios';

export default {
    components: {
    HeaderComponent,
    MainComponent,
    FooterComponent
},
data (){
    return {
        searchText: '',
        movies: []
    }
},
methods: {
    search() {
        console.log(this.searchText)

        axios.get('https://api.themoviedb.org/3/search/movie',{
            params: {
                api_key: '613268612b38b5bd860bdf0ba8565e74',
                query: this.searchText
            }
        })
        .then(response => {
            console.log(response.data.results);
            this.movies = response.data.results;
        });
    }
}
};

</script>

<template>


    <header>
        <input 
            type="text" 
            placeholder="cerca..."
            v-model="searchText">
        <button @click="search()">
            Cerca
        </button>
    </header>

    <main>
        <ul>
            <li v-for="(movie, i) in movies" :key="i">
                <ol>
                    <li>{{ movie.title }}</li>
                    <li>{{ movie.original_title }}</li>
                    <li>{{ movie.original_language }}</li>
                    <li>{{ movie.vote_average }}</li>
                </ol>
            </li>
        </ul>
    </main>


    <!-- <HeaderComponent/>
    <MainComponent />
    <FooterComponent /> -->
</template>

<style lang="scss">
@use "./assets/scss/main.scss";

</style>
