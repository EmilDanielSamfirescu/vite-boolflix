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
    <div>
        <ol>
            <li>
                <!-- ?? è un operatore binario, funziona tipo l'OR -->
                {{ elementData.title ?? elementData.name}}
            </li>

            <li>
                {{ elementData.original_title ?? elementData.original_name}}
            </li>

            <li>
                <img :src="getFlag(elementData.original_language)" :alt="elementData.original_language.toUpperCase()">
            </li>

            <li>
                {{ elementData.vote_average }}
            </li>

        </ol>
    </div>
</template>

<style lang="scss" scoped>
img {
        width: 30px;
    }
</style>
