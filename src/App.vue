<template>
	<div id="app">
		<Health :playerHealth="playerHealth" :monsterHealth="monsterHealth"/>
		<Control 
			:gameStatus="gameIsRunning" 
			@gameStatusChange="startGame"
			@attack="attack"
			@specialAttack="specialAttack"
			@heal="heal"
			@giveUp="giveUp"/>
		<Message
			v-if="turns.length > 0"
			:logs="turns"
		/>
	</div>
</template>

<script>
	import Health from './components/Health/Health'
	import Control from './components/Control/Control'
	import Message from './components/Message/Message'
	export default {
		name: 'App',
		components: {Health,Control,Message},
		data() {
			return {
				playerHealth: 100,
				monsterHealth: 100,
				gameIsRunning: false,
				turns: []
			}
		},
		methods: {
			startGame: function () {
                this.gameIsRunning = true;
                this.playerHealth = 100;
                this.monsterHealth = 100;
            },
			attack: function () {
				this.monsterAttacks(3,10);
				this.playerAttacks(5,12)
			},
			specialAttack: function () {
				this.monsterAttacks(10,20)
				this.playerAttacks(5,12)
			},
			heal: function () {
				if (this.playerHealth <= 90)
					this.playerHealth += 10
				else
					this.playerHealth = 100
			},
			giveUp: function () {
				this.gameIsRunning = false;
				this.playerHealth = 100;
				this.monsterHealth = 100;
				this.turns = []
			},
			monsterAttacks: function (min,max) {
				let damage = this.caculateDamage(min,max);
				this.monsterHealth -= damage
				this.turns.unshift({
					isPlayer: true,
					text: 'Player hit monster for ' + damage
				})
				if (this.checkWin()) return
			},
			playerAttacks: function (min,max) {
				let damage = this.caculateDamage(min,max);
				this.playerHealth -= damage
				this.turns.unshift({
					isPlayer: false,
					text: 'Monster hit player for ' + damage
				})
				this.checkWin();	
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
	}
</script>

<style>
	@import './assets/css/foundation.min.css';
	@import './assets/css/app.css';	
</style>
