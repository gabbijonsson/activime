<template>
	<div class="content">
		<div class="containerItems"><a @click="handleSelect($event)" v-for="worktask in worklist" :key="worktask.id" :id="worktask.id" :title="worktask.title">
			{{ worktask.title }}
		</a></div>
		<WorkListDisplay v-show="!keepHidden"/>
	</div>
</template>

<script>
 import {eventBus} from "../main";
 import WorkListDisplay from './WorkListDisplay'
export default {
	name: 'BeforeSprint',
	data: () => ({
		worklist: [],
		keepHidden: true,
		currentTask: String,
		showDuringSprint: true,
	}),
	components: {WorkListDisplay},
	methods: {
		handleSelect(event){
			console.log('I want to work with you!', event.target.title);
			console.log(event.target.id);
			console.log(event);
			this.currentTask = event.target.title;
			eventBus.$emit('currentTask', this.currentTask)
			this.$emit('showDuing', this.showDuringSprint)
		},
		reciveList(){
			this.worklist = eventBus.$emit('workList', this.worklist)			
		},
	},
	created(){
		eventBus.$on('workList', (recivedList) => {
			this.worklist = recivedList
			console.log(this.worklist);
			console.log(recivedList);			
		}),
		console.log('created', this.worklist);
			console.log('created again', this.recivedList);
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