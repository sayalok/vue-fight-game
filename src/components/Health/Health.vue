<template>
    <section class="row">
        <SinglePlayerHealth :playerName="playerOneName" :playerHealth="playerHealth"/>
        <SinglePlayerHealth :playerName="playerTwoName" :playerHealth="monsterHealth"/>
    </section>
</template>
<script>
	import SinglePlayerHealth from './SinglePlayerHealth'
    export default {
        name: 'Health',
        data() {
            return {
                playerOneName: "ME",
                playerTwoName: "Monster"
            }
        },
        props: ['playerHealth','monsterHealth'],
        components: {
            SinglePlayerHealth
        }
    }
</script>