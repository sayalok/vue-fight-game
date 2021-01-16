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
		<Message/>
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
				this.monsterAttacks(3,10);
				this.playerAttacks()
			},
			specialAttack: function () {
				this.monsterAttacks(10,20)
				this.playerAttacks()
			},
			heal: function () {
				if (this.playerHealth <= 90)
					this.playerHealth += 10
				else
					this.playerHealth = 100
			},
			giveUp: function () {
                this.gameIsRunning = false;
			},
			monsterAttacks: function (min,max) {
				this.monsterHealth -= this.caculateDamage(min,max)
				if (this.checkWin()) return
			},
			playerAttacks: function () {
				this.playerHealth -= this.caculateDamage(5,12)
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
