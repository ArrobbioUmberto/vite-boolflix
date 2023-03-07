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
        <Movies v-for="element in store.movie" :key="element.id" :el="element"></Movies>
        <Tvseries v-for="series in store.series" :key="series.id" :Tvseries="series"></Tvseries>
    </div>
</template>

<style lang="scss" scoped>
img {
    width: 200px;
}
</style>