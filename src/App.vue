<template>
	<div id="app">
		<Health :playerHealth="playerHealth" :monsterHealth="monsterHealth"/>
		<Control 
			:gameStatus="gameIsRunning" 
			@gameStatusChange="startGame"
			@attack="attack"/>
		<Message/>
	</div>
</template>

<script>
	import Health from './components/Health/Health'
	import Control from './components/Control/Control'
	import Message from './components/Message/Message'
	export default {
		name: 'App',
		data() {
			return {
				playerHealth: 100,
				monsterHealth: 100,
				gameIsRunning: false
			}
		},
		methods: {
			startGame: function () {
                this.gameIsRunning = true;
                this.playerHealth = 100;
                this.monsterHealth = 100;
            },
			attack: function () {
				var damage = this.caculateDamage(3,10)
				this.monsterHealth -= damage

				if (this.checkWin()) return

				damage = this.caculateDamage(5,12)
				this.playerHealth -= damage
				
				this.checkWin();
			},
			specialAttack: function () {
				
			},
			heal: function () {
				
			},
			giveUp: function () {
				
			},
			caculateDamage: function (min,max) {
				return Math.max(Math.floor(Math.random() * max) + 1, min)	
			},
			checkWin: function () {
				if (this.monsterHealth <= 0) {
					confirm('You won! New Game?') ? this.startGame() : this.gameIsRunning = false
					return true
				}else if (this.playerHealth <= 0) {
					confirm('You Lost! New Game?') ? this.startGame() : this.gameIsRunning = false
					return true
				}
				return false
			}
		},
		components: {Health,Control,Message}
	}
</script>

<style>
	@import './assets/css/foundation.min.css';
	@import './assets/css/app.css';	
</style>
