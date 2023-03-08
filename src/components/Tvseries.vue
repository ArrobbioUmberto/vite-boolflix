<script>
import '@fortawesome/fontawesome-free/css/all.min.css';
export default {
    props: {
        Tvseries: {
            type: Object,
            required: true,
        }
    },
    methods: {
        getFlagImage(country) {
            switch (country) {
                case 'en':
                    return '/img/uk.jpg'
                case 'it':
                    return '/img/ita.png'
                case 'ja':
                    return '/img/jap.png'
                default:
                    return '/img/world.jpg'
            }
        },
        getStarIcon(index) {
            const voto = Math.ceil(this.Tvseries.vote_average / 2);
            switch (index) {
                case 1:
                    return voto >= 1 ? 'full' : '';
                case 2:
                    return voto >= 2 ? 'full' : '';
                case 3:
                    return voto >= 3 ? 'full' : '';
                case 4:
                    return voto >= 4 ? 'full' : '';
                case 5:
                    return voto >= 5 ? 'full' : '';
                default:
                    return '';
            }
        }
    }
}
</script>
<template>
    <div class="col">
        <ul>
            <li>
                <img class="poster"
                    :src="Tvseries.poster_path ? `https://image.tmdb.org/t/p/w342/${Tvseries.poster_path}` : '/img/default.webp'">
                <h2>{{ Tvseries.name }}</h2>
                <h2>{{ Tvseries.original_name }}</h2>
                <h3>{{ Math.ceil(Tvseries.vote_average / 2) }}</h3>
                <div>
                    <span>
                        <i v-for="n in 5" :key="n" :class="['fa', 'fa-star', getStarIcon(n)]"></i>
                    </span>
                </div>
                <img :src="getFlagImage(Tvseries.original_language)" alt="Flag">
            </li>
        </ul>
    </div>
</template>
<style lang="scss" scoped>
.poster {
    width: 100%;
}

li {
    list-style-type: none;
}

ul {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    gap: 10px;
}

span {
    font-size: 24px;
    font-weight: bold;
}

img {
    width: 50px;
}

.col {
    display: flex;
    flex-basis: 20%;
    align-items: center;
    justify-content: flex-start;
}

.full {
    color: gold;
}
</style>