<script>
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
                <h4>{{ el.vote_average }}</h4>
                <img class="flag" :src="getFlagImage(el.original_language)" alt="">
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

.flag {
    width: 50px;
}

.col {
    display: flex;
    flex-basis: 20%;
    flex-shrink: 0;
    align-items: center;
}
</style>