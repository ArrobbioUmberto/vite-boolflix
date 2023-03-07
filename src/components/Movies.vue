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
                <h3>{{ el.title }}</h3>
                <h3>{{ el.original_title }}</h3>
                <h4>{{ el.vote_average }}</h4>
                <img :src="getFlagImage(el.original_language)" alt="Flag">
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
    flex-shrink: 0;
    align-items: center;
}
</style>