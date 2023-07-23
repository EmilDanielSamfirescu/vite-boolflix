<script >
export default {
    name: "SingleElement",
    data (){
        return {

        }
    },
    props:{
        elementData: {
            type: Object,
            default: null
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
    <div class="card-container">
            <div class="poster-container">
                <img v-if="elementData.backdrop_path == null" src="https://img.whaleshares.io/wls-img/einstei1/d765e65f432e7e6f0d062616d19364ecdc5631da.png" alt="">
                <img v-else :src="`https://image.tmdb.org/t/p/w342/${elementData.poster_path}`" alt="">
            </div>
            
            <div class="description-container">

                <div>
                    <span>Titolo: </span> 
                    {{ elementData.title ?? elementData.name}}
                </div>

                <div>
                    <span>Titolo Originale: </span> 
                    {{ elementData.original_title ?? elementData.original_name}}
                </div>

                <div>
                    <span>Lingua: </span> 
                    <img class="flag" :src="getFlag(elementData.original_language)" :alt="elementData.original_language.toUpperCase()">
                </div>

                <div>
                    <!-- {{ elementData.vote_average }} -->
                    <span>Voto: </span>
                    <span v-for="numero in Math.ceil(elementData.vote_average / 2)" :key="numero"><i class="fa-solid fa-star"></i></span>
                    <span v-for="numero in (5 - (Math.ceil(elementData.vote_average / 2)))" :key="numero"><i class="fa-regular fa-star"></i></span>
                </div>

                <div>
                    <span>Overview: </span> 
                    {{ elementData.overview }}
                </div>

            </div>
    </div>
</template>

<style lang="scss" scoped>


img {
    max-width: 342px;
    cursor: pointer;
    &.flag {
        width: 40px;
    }
}

.poster-container > img {
    transition: all 0.4s;
}

.card-container{
    position: relative;
    background-color: black;
    overflow: auto;
}

.description-container{
    display: none;
    color: white;
    width: 342px;
    position: absolute;
    margin-top: 20px;
    padding: 15px;
    z-index: 4;
    top: 0;
    left: 0;
    span{
        font-weight: bold;
    }
}
.card-container:hover .description-container{
    display: block;
}

.card-container:hover .poster-container > img{
    opacity: 0;
}
</style>
