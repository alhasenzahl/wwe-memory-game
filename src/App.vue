<template>
    <div class="container">
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
    </div>
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
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
    }

    html {
        box-sizing: border-box;
        font-size: 10px;
    }

    *,
    *::before,
    *::after {
        box-sizing: inherit;
    }

    html,
    body {
        width: 100%;
        height: 100%;
        margin: 0;
        padding: 0;
    }

    body {
        background-image: url('https://1.bp.blogspot.com/-qTwY85_O668/WAnKTDSTvUI/AAAAAAAAB2A/U3VL7wXsvJESu1CSJ304m7C8WQV7YZPzACLcB/s1600/1.JPG');
        background-size: cover;
        font-family: 'Coda', cursive;
    }

    .container {
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
        height: 100vh;
    }

    h1 {
        font-family: 'Open Sans', sans-serif;
        font-weight: 300;
        color: white;
        font-size: 3rem;
        padding: 0 2.7rem;
        text-align: center;
    }

    /*
    * Styles for the deck of cards
    */

    .deck {
        max-width: 66rem;
        min-height: 54.8rem;
        width: calc(100% - 2rem);
        height: calc(100% - 2rem);
        background: linear-gradient(160deg, #CC281D 0%, #FF3424 100%);
        padding: 2rem 0;
        border-radius: 1rem;
        box-shadow: 1.2rem 1.5rem 2rem 0 rgba(46, 61, 73, 0.5);
        display: grid;
        padding-inline-start: 0;
        grid-template-columns: 1fr 1fr;
        grid-gap: 2rem 0;
        overflow: scroll;
    }

    .deck .card {
        max-height: 12.5rem;
        max-width: 12.5rem;
        background: #2e3d49;
        font-size: 0;
        color: #ffffff;
        border-radius: .8rem;
        cursor: pointer;
        justify-self: center;
        align-self: center;
        box-shadow: .5rem .2rem 2rem 0 rgba(46, 61, 73, 0.5);
    }

    .deck .card .card-back,
    .deck .card .card-front {
        width: 100%;
        height: auto;
        border-radius: .8rem;
    }

    .deck .card .card-front {
        filter: grayscale(100%) contrast(70%);
    }

    .deck .card-button {
        background: none;
        border: none;
        padding: 0;
        cursor: pointer;
    }

    /*
    * Styles for the Score Panel
    */

    .score-panel {
        text-align: left;
        width: 100%;
        max-width: 34.5rem;
        margin-bottom: 1rem;
        color: white;
        padding: 0 2rem;
        font-size: 1.5rem;
    }

    .score-panel .stars {
        margin: 0;
        padding: 0;
        display: inline-block;
        margin: 0 .5rem 0 0;
    }

    .score-panel .restart {
        float: right;
        cursor: pointer;
        color: white;
        background: none;
        border: none;
        font-size: 1.5rem;
    }

    .star-icon {
        list-style: none;
        display: inline-block;
        color: white;
    }

    #stop-watch {
        color: white;
        font-size: 1.5rem;
    }

    .timer-wrap {
        margin-bottom: 2rem;
    }

    .modal-background {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: rgba(0, 0, 0, 0.438);
    }

    .modal-body {
        position: relative;
        max-width: 40rem;
        width: calc(100% - 2rem);
        top: 50%;
        left: 50%;
        background: #fff;
        transform: translate(-50%, -50%);
        display: flex;
        border-radius: 1rem;
        min-height: 35rem;
    }

    .modal-body_container {
        width: 100%;
    }

    .modal-heading {
        padding: 0;
        font-size: 2.5rem;
    }

    .modal-title {
        text-align: center;
    }

    .modal-main {
        padding: 3rem 0;
        margin: auto;
        display: block;
        border-top: 1px solid grey;
        border-bottom: 1px solid grey;
        font-size: 1.6rem;
    }

    .modal-main_title {
        display: flex;
        width: 100%;
        justify-content: center;
        padding: 0 2rem;
    }

    .modal-buttons {
        display: block;
        margin: auto;
        padding-top: 5rem;
        width: 20rem;
    }

    .quit-game {
        width: 7.5rem;
        margin-right: 5rem;
        padding: 1rem 0;
        border-radius: .8rem;
        font-size: 1.2rem;
    }

    .play-again {
        width: 7.5rem;
        padding: 1rem 0;
        border-radius: .8rem;
        font-size: 1.2rem;
    }

    .hide {
        display: none;
    }

    @media only screen and (min-width: 480px) {
    .deck {
            grid-template-columns: 1fr 1fr 1fr;
        }

        .score-panel {
            padding: 0;
        }
    }

    @media only screen and (min-width: 600px) {
    .deck {
            grid-template-columns: 1fr 1fr 1fr 1fr;
        }
    }
</style>
