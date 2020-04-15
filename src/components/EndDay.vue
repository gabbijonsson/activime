<template>
	<div class="end-day--container" @click="handleEndDay">
		<p>Klar för idag?</p>
		<img  src="../assets/img/icon--action-endday.svg" alt="Avsluta-ikon">
	</div>
</template>

<script>
export default {
	name: 'EndDay',
	data: () => ({
		finishDay: Boolean
	}),
	methods: {
		handleEndDay(){
			this.finishDay = true
			this.$emit('theEnd', this.finishDay)
		}
	}
}
</script>

<style scoped>
p {
	display: inline;
	font-size: 2em;
}
img{
	margin-right: 3em;
}
.end-day--container {
	cursor: pointer;
  display: flex;
  position: fixed;
  justify-content: flex-end;
  bottom: 10em;
  width: 100vw;
}

</style>