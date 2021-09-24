<template>
    <button class="card-button">
        <img
            :src="card.front"
            alt="Charlotte vs Sasha Banks at Hell in a Cell 2016"
            class="card-front"
            v-if="! card.isOpen && ! card.isShown && ! card.isMatched"
            :class="{
                'open': card.isOpen,
                'show': card.isShown,
                'match': card.isMatched
            }"
        />
        <img
            :src="card.back"
            :alt="card.altText"
            class="card-back"
            v-if="card.isOpen || card.isShown || card.isMatched"
            :class="{
                'open': card.isOpen,
                'show': card.isShown,
                'match': card.isMatched
            }"
        />
    </button>
</template>

<script>
export default {
    name: 'Card',
    props: ['card'],
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
    margin: 40px 0 0;
}
ul {
    list-style-type: none;
    padding: 0;
}
li {
    display: inline-block;
    margin: 0 10px;
}
a {
    color: #42b983;
}
</style>
