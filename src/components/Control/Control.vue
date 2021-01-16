<template>
    <div>
        <section class="row controls" v-if="!gameStatus">
			<div class="small-12 columns">
                <Button
                    id="start-game"
                    value="START NEW GAME"
                    @clickEvent="startGame"
                />
			</div>
		</section>
		<section class="row controls" v-else>
			<div class="small-12 columns">
                <Button
                    id="attack"
                    value="ATTACK"
                    @clickEvent="attack"
                />
                <Button
                    id="special-attack"
                    value="SPECIAL ATTACK"
                    @clickEvent="specialAttack"
                />
                <Button
                    id="heal"
                    value="HEAL"
                    @clickEvent="heal"
                />
                <Button
                    id="give-up"
                    value="GIVE UP"
                    @clickEvent="giveUp"
                />
			</div>
		</section>
    </div>
</template>
<script>
    import Button from '../Button/Button'
    export default {
        name: 'Control',
        components: {Button},
        props: ['gameStatus'],
        methods: {
            startGame: function () {
                this.$emit('gameStatusChange')
            },
            attack: function () {
                this.$emit('attack')
            },
            specialAttack: function () {
                this.$emit('specialAttack')
            },
            heal: function () {
                this.$emit('heal')
            },
            giveUp: function () {
                this.$emit('giveUp')
            },
        },
    }
</script>
<style>

</style>