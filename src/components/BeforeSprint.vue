<template>
	<div class="content">
			<!-- //! Tid att utföra en "ToDo" ligger i "event.target.type"! -->
		<div class="containerItems"><a :type="toDoList.estTime" :id="toDoList.id" @click="handleSelect">
			{{ toDoList.name }}
		</a></div>
	</div>
</template>

<script>
export default {
	name: 'BeforeSprint',
	props: {
		toDoList: Object(null),
	},
	methods: {
		handleSelect(event){
			console.log('hello there!');
			console.log(event.target.id);
			console.log(event);
		},
		
	}
}
</script>

<style scoped>
.containerItems{
	margin-top: 2em;
	padding: 1em;
}
a:hover{
	cursor: pointer;
	text-decoration: underline;
}
</style>