<script>
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
        }
    }
}
</script>
<template>
    <div class="col">
        <ul>
            <li>
                <h2>{{ Tvseries.name }}</h2>
                <h2>{{ Tvseries.original_name }}</h2>
                <h3>{{ Tvseries.vote_average }}</h3>
                <img :src="getFlagImage(Tvseries.original_language)" alt="Flag">
            </li>
        </ul>
    </div>
</template>
<style lang="scss" scoped>
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
</style>