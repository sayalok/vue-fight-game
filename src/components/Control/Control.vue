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
				<!-- <button id="attack">ATTACK</button> -->
				<button id="special-attack">SPECIAL ATTACK</button>
				<button id="heal">HEAL</button>
				<button id="give-up">GIVE UP</button>
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
            }
        },
    }
</script>
<style>

</style>