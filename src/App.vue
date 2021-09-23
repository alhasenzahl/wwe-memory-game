<template>
    <ul class="deck">
        <li
            class="card"
            :key="card.key"
            v-for="card in cardList"
        >
            <Card
                :card="card"
            />
        </li>
    </ul>
</template>

<script>
import Card from './components/Card.vue';

export default {
    name: 'App',
    components: {
        Card,
    },
    data() {
        return {
            cardList: [],
        };
    },
    methods: {
        getCardList() {
            fetch('cards.json')
                .then((response) => response.json())
                // eslint-disable-next-line no-return-assign
                .then((data) => this.cardList = data);
        },
    },
    created() {
        this.getCardList();
    },
};
</script>

<style lang="scss">
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}
</style>
