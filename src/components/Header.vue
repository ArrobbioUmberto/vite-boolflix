<script >
import store from '../store'
import axios from 'axios'
export default {
    components: {
        // Movies
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
                });
        },
        getSeries() {
            const key = this.store.key;
            const search = this.store.search;
            axios.get("https://api.themoviedb.org/3/search/tv", {
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
                    this.store.series = res.data.results;
                });
        }
    },

}
</script>

<template>
    <div class="container">
        <div class="row">
            <img src="/img/logo-netflix.webp" alt="">
            <input type="text" placeholder="Cerca il tuo film/serieTv" v-model="store.search"
                @keyup.enter="getMovie(), getSeries()">
            <button @click="getMovie(), getSeries()" class="button"> Cerca</button>
        </div>

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

.row {
    padding: 20px;
}

img {
    width: 50px;
    margin-right: 20px;
}

.row {
    display: flex;
    align-items: center;
}
</style>