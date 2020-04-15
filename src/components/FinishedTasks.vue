<template>
	<div class="content">
		<div class="container-finishedlist"
		v-for="task in finishedTasks" :key="task.id">
			{{ FinishedTasks.title }}
		</div>

	</div>
</template>

<script>
export default {
	name: 'FinishedTasks',
	methods: {

	},
	data: () => ({
		finsishedTasks: [],
	}),
}
</script>

<style>

</style>