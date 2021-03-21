<template>
	<div id="spells">
	<div class='mainContent'>
		<div id="input1">
			<label><strong>Enter a Spell Name: </strong></label>
			<input id="dndInput" type="text" v-model='dndSpell'><br/>
			
			<label><strong>Enter a Spell Description (If Adding Your Own): </strong></label>
			<input type="text" v-model='spellDesc'><br/>
			
			<button id="dndSubmit" v-on:click="addSpelltoList(dndSpell, spellDesc)">Submit</button>
		</div>
		<div id="selectExplanation">
			<p>Enter the name of a D&D spell, or make up a spell.</p>
			<p>Examples: Acid Arrow, Fireball, Fire Bolt, Fly, Sanctuary</p>
		</div>
		
		<div id="dndResults">
			<SpellList :spells="spells" />
		</div>
		</div>
		
		
		<br/>
		<br/>
		<br/>
		<br/>
		<div class='footer'>
			<p><a href='https://github.com/VoidDead/creativeproject3'>https://github.com/VoidDead/creativeproject3</a></p>
		</div>
	</div>
</template>

<script>
	import SpellList from "../components/SpellList.vue"
	export default 
	{
		name: 'Spells',
		components: 
		{
			SpellList
		},
		data() {
			return {
				spellDesc:'',
				dndSpell:'',
			}
		},
		computed: 
		{
			spells() 
			{
				return this.$root.$data.spellHistory;
			}
		},
		methods: 
		{
			addSpelltoList: function(spell, spellDesc) 
			{
				if (spell) {
					let spellURL = spell.replace(/\s/g , "-");
					const url = "https://www.dnd5eapi.co/api/" + "spells/" + spellURL;
					fetch(url)
						.then((response) => {
							console.log(response);
							if (response.status === 404)
							{
								let newSpell = JSON.parse('{ "name":"' + spell + '", "desc":"' + spellDesc + '" }');
								console.log(newSpell);
								this.$root.$data.spellHistory.push(newSpell);
							}
							return response.json();
						}).then((json) => {
							if (json) {
								let newSpell = JSON.parse('{ "name":"' + json.name + '", "desc":"' + json.desc + '" }');
								console.log(newSpell);
								this.$root.$data.spellHistory.push(newSpell);
							}
						});
					}
				else {
					console.log("No spell given.");
				}
			},
		},
	}
</script>

<style scoped>
</style>
