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
                }
            })
                .then((res) => {
                    console.log(res);
                    console.log(res.data);
                    console.log(res.data.results);
                    this.store.movie = res.data.results;
                    console.log(this.store.movie)
                });
        }
    },
    created() {
        this.getMovie();
    },
}
</script>

<template>
    <div class="container">
        <Movies v-for="element in store.movie" :key="element.id" :el="element"></Movies>
    </div>
</template>

<style lang="scss" scoped>
img {
    width: 200px;
}
</style>