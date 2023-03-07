<script>
export default {
    props: {
        el: {
            type: Object,
            required: true,
        }
    }
}
</script>
<template>
    <ul>
        <li>
            <h2>{{ el.title }}</h2>
            <h2>{{ el.original_title }}</h2>
            <h3>{{ el.vote_average }}</h3>
            <h4>{{ el.original_language }}</h4>
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