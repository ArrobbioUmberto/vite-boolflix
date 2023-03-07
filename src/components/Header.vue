<script >
import store from '../store'
import axios from 'axios'
import Movies from './Movies.vue'
export default {
    components: {
        Movies
    },
    data() {
        return {
            store
        };
    },
    methods: {
        getMovie() {
            const key = this.store.key;
            const search = this.store.search;
            axios.get("https://api.themoviedb.org/3/search/movie", {
                params: {
                    api_key: key,
                    query: search,
                    language: 'it-IT'
                }
            })
                .then((res) => {
                    console.log(res);
                    console.log(res.data);
                    console.log(res.data.results);
                    this.store.movie = res.data.results;
                    // this.store.vote = res.data.results.vote_average
                    // console.log(res.data.results[].vote_average)
                });
        }
    },
    computed: {
        searchText() {
            return this.store.search
        }
    },

}
</script>

<template>
    <div class="container">
        <input type="text" placeholder="Cerca il tuo film/serieTv" v-model="store.search" @keyup.enter="getMovie()">
        <button class="button"> Cerca</button>
    </div>
</template>

<style lang="scss" scoped>
.button {
    margin: 0 10px;
    font-size: 16px;
    font-weight: bold;
    color: white;
    padding: 5px 10px;
    background-color: cornflowerblue;
    border: none;
    border-radius: 25px;
}
</style>