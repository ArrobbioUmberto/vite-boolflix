<script>
import '@fortawesome/fontawesome-free/css/all.min.css';
export default {
    props: {
        el: {
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
            const voto = Math.ceil(this.el.vote_average / 2);
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
                    :src="el.poster_path ? `https://image.tmdb.org/t/p/w342/${el.poster_path}` : '/img/default.webp'">
                <h3>{{ el.title }}</h3>
                <h3>{{ el.original_title }}</h3>
                <div class="votation">
                    <h4>{{ Math.ceil(el.vote_average / 2) }}</h4>
                    <span>
                        <i v-for="n in 5" :key="n" :class="['fa', 'fa-star', getStarIcon(n)]"></i>
                    </span>
                </div>
                <img class="flag" :src="getFlagImage(el.original_language)" alt="">
            </li>
        </ul>
    </div>
</template>
<style lang="scss" scoped>
h3,
h4 {
    margin: 5px;
}

.votation {
    display: flex;
    font-size: 24px;
    align-items: center;
    justify-content: space-between;
}

.poster {
    width: 100%;
}

li {
    list-style-type: none;
    display: flex;
    flex-direction: column;
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



.flag {
    width: 50px;
}

.col {
    display: flex;
    flex-basis: 20%;
    flex-shrink: 0;
    align-items: center;
}

.full {
    color: gold;
}
</style>