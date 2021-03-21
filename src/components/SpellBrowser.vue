<template>
<div class="wrapper">
  <div class="spells">
    <div class="spell" v-for="spell in spells" :key="spell.id">
      <div class="info">
        <h1>{{spell.name}}</h1>
		<p>{{spell.desc}}</p>
      </div>
    </div>
  </div>
</div>
</template>

<script>
export default {
  name: 'SpellList',
  props: {
    spells: Array
  },
}
</script>

<style scoped>
.spellTitle {
	text-align: center;
	font-size: 24px;
}
.spellDesc {
}

.wrapper {
  display: flex;
  align-items: center;
  justify-content: center;
}

.info {
  background: #F2927D;
  color: #000;
  padding: 10px 30px;
  border: solid 2px #fff;
}

.info h1 {
  font-size: 24px;
}

.info h2 {
  font-size: 14px;
}

.info p {
  margin: 12px;
}

button {
  height: 50px;
  background: #000;
  color: white;
  border: none;
}

.auto {
  margin-left: auto;
}
</style>