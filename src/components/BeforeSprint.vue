<template>
	<div class="content">
		<div class="containerItems"><a @click="handleSelect(worktask)" v-for="worktask in worklist" :key="worktask.id" :id="worktask.id" :title="worktask.title">
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
		currentTask: '',
		showDuringSprint: true,
	}),
	components: {WorkListDisplay},
	methods: {
		handleSelect(task){
			console.log('task selected: ' + task.title)
			localStorage.setItem('currentTask', JSON.stringify(task))
			this.$emit('showDuring', this.showDuringSprint)

		},		
		reciveList(){
			this.worklist = eventBus.$emit('workList', this.worklist)			
		},
	},
	created(){
		eventBus.$on('theCurrentTask', (theSelected) => {
			this.currentTask = theSelected;
			console.log(theSelected);
			console.log(this.currentTask);
			
			
		}),
		eventBus.$on('workList', (recivedList) => {
			this.worklist = recivedList;
			console.log(this.worklist);
			console.log(recivedList);
		})
	},
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