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
                    return ''
            }
        }
    }
}
</script>
<template>
    <ul>
        <li>
            <span>SerieTV</span>
            <h2>{{ Tvseries.name }}</h2>
            <h2>{{ Tvseries.original_name }}</h2>
            <h3>{{ Tvseries.vote_average }}</h3>
            <img :src="getFlagImage(Tvseries.original_language)" alt="Flag">
        </li>
    </ul>
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
</style>