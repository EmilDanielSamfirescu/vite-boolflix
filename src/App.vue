<script >
import HeaderComponent from './components/HeaderComponent.vue';
import MainComponent from './components/MainComponent.vue';
import FooterComponent from './components/FooterComponent.vue';
import axios from 'axios';
import {store} from './store.js';

export default {
    components: {
    HeaderComponent,
    MainComponent,
    FooterComponent
},
data (){
    return {
        store
    }
},
methods: {
    search() {
        console.log(this.store.searchText)

        axios.get('https://api.themoviedb.org/3/search/movie',{
            params: {
                api_key: '613268612b38b5bd860bdf0ba8565e74',
                query: this.store.searchText
            }
        })
        .then(response => {
            console.log(response.data.results);
            this.store.movies = response.data.results;
        });
    }
}
};

</script>

<template>

    <HeaderComponent @performSearch="search()"/>

    <MainComponent />

    <FooterComponent />

</template>

<style lang="scss">
@use "./assets/scss/main.scss";

</style>
