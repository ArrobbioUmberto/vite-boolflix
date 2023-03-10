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
            const voto = Math.round(this.Tvseries.vote_average / 2);
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
            <li class="poster-box">
                <img class="poster"
                    :src="Tvseries.poster_path ? `https://image.tmdb.org/t/p/w342/${Tvseries.poster_path}` : '/img/default.webp'">
            </li>
            <li class="text-box">
                <h2>{{ Tvseries.name }}</h2>
                <h2>{{ Tvseries.original_name }}</h2>
                <div class="votation">
                    <h3>{{ Math.round(Tvseries.vote_average / 2) }}</h3>
                    <span>
                        <i v-for="n in 5" :key="n" :class="['fa', 'fa-star', getStarIcon(n)]"></i>
                    </span>
                </div>
                <img class="flag" :src="getFlagImage(Tvseries.original_language)" alt="Flag">
                <div class="overview">
                    <p><b>Overview:{{ Tvseries.overview }}</b></p>
                </div>
            </li>
        </ul>
    </div>
</template>
<style lang="scss" scoped>
.overview {
    height: 200px;
    overflow: auto;
}

::-webkit-scrollbar {
    width: 10px;
}

.votation {
    display: flex;
    font-size: 24px;
    align-items: center;
    justify-content: space-between;
}

h3,
h2 {
    margin: 5px;
}


.poster {
    width: 100%;
}

.poster-box {
    height: 400px;
}

.text-box {
    display: none;
    overflow: auto;
}

ul:hover .poster-box {
    display: none;
}

ul:hover .text-box {
    display: block;
}

li {
    list-style-type: none;
    display: flex;
    flex-direction: column;
    height: 400px;
}

ul {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    padding: 0;
    margin: 0;
    gap: 10px;
}

span {
    font-size: 24px;
    font-weight: bold;
}



.flag {
    width: 50px;
}

.col {
    display: flex;
    flex-basis: 20%;
    align-items: center;
}

.full {
    color: gold;
}
</style>