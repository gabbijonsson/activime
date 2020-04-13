<template>
	<div class="content">
			//! Tid att utföra en "ToDo" ligger i "event.target.type"!
		<div class="containerItems"><a :type="toDoList.estTime" :id="toDoList.id" v-on:click="select" @click="handleSelect">
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
		handleSelect(){
			console.log('hello there!');
			
		},
		select(event){
			console.log(event.target.id);
			console.log(event);
			
			
		}
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
}
</style>