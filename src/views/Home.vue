<template>
	<div id='Home'>
  
	<div class='mainContent'>
	<h1>Special Spells</h1>
	
	<p>This is a website for mystical, magical spells. You can add spells in the 'Add Spells' page, using D&D spells or by making your own spells. You can then view the spells here.</p>
	
	<SpellBrowser :spells="spells" />
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
// @ is an alias to /src

import SpellBrowser from "../components/SpellBrowser.vue"

export default {
	name: 'Home',
	components: 
		{
			SpellBrowser
		},
	computed: 
		{
			spells() 
			{
				return this.$root.$data.spellHistory;
			}
		},
}

</script>

<style>
body {
	margin: 0;
	width: 100%;
}

.mainContent {
	max-width: 960px;
	margin: auto;
}

.footer {
	text-align: center;
	position: fixed;
	width: 100%;
	bottom:0;
	background-color: #522;
	padding-top: 15px;
	padding-bottom: 15px;
}
.footer a {
	color: #bef;
}
.footer a:hover {
	color: #1ee;
}
.footer a:active {
	color: #bfb;
}
</style>