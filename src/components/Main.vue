<script >
import store from '../store'
import axios from 'axios'
import Movies from './Movies.vue'
import Tvseries from './Tvseries.vue'
export default {
    components: {
        Movies,
        Tvseries
    },
    data() {
        return {
            store
        };
    },
    methods: {

    },
    computed: {
        searchText() {
            return this.store.search
        }
    },
    watch: {
        searchText(newvalue, Oldvalue) {
            console.log('cambio di search', newvalue, Oldvalue)
        }
    }
}
</script>

<template>
    <div class="container">
        <div class="row">
            <h1>Film</h1>
            <Movies v-for="element in store.movie" :key="element.id" :el="element"></Movies>
        </div>
        <div class="row">
            <h1>SerieTV</h1>
            <Tvseries v-for="series in store.series" :key="series.id" :Tvseries="series"></Tvseries>
        </div>

    </div>
</template>

<style lang="scss" scoped>
img {
    width: 200px;
}

.row {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: space-between;
    align-items: center;
    color: white;
}

h1 {
    width: 100%;
}
</style>