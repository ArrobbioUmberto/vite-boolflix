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
                    return ''
            }
        }
    }
}
</script>
<template>
    <ul>
        <li>
            <span>Film</span>
            <h2>{{ el.title }}</h2>
            <h2>{{ el.original_title }}</h2>
            <h3>{{ el.vote_average }}</h3>
            <img :src="getFlagImage(el.original_language)" alt="Flag">
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
</style>