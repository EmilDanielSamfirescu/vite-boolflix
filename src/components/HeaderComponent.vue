<script >
import {store} from '../store.js';
export default {
    name: "HeaderComponent",
data (){
    return {
        store
    }
},
methods: {
    
}
};
</script>

<template>

    <header>

        <div class="container">
            <div class="d-flex justify-content-between align-items-center">
                <h1>
                    BOOTFLIX
                </h1>

                <div>
                    <input 
                    type="text" 
                    placeholder="cerca..."
                    v-model="store.searchText">

                    <button 
                        @click="$emit('performSearch')">
                            Cerca
                    </button>
                </div>
            </div>
        </div>

    </header>

</template>

<style lang="scss" scoped>
    header {
        background-color: rgb(33, 33, 33);
        color: white;
        height: 10vh;
        padding: 10px;

        h1 {
            margin-bottom: 0;
        }
    }
</style>