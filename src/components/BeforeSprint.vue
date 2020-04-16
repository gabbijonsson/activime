<template>
	<div class="content">
		<div class="containerItems">
			<h2>Vilken uppgift vill du jobba med idag?</h2>
			<a @click="handleSelect(worktask)" v-for="worktask in avaliableWorkList" :key="worktask.id" :id="worktask.id" :title="worktask.title">
			{{ worktask.title }}
			</a>
		</div>
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
		avaliableWorkList: [],
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
		showAvaliable(){
			this.avaliableWorkList = this.worklist.filter(function(task){
				return task.finished == false;
			});
			console.log('Tasks that are avaliable', this.avaliableWorkList);			
			
		}
	},
	mounted(){
		
		if(localStorage.getItem('worklist')){
			this.worklist = JSON.parse(localStorage.getItem('worklist'));
			console.log('inside mounted if');
			
			this.showAvaliable()
		}else{
			console.log('inside mounted else');
			
			eventBus.$on('workList', (recivedList) => {
			this.worklist = recivedList;
			console.log(this.worklist);
			console.log(recivedList);
			this.showAvaliable()
			eventBus.$on('theCurrentTask', (theSelected) => {
				this.currentTask = theSelected;
				console.log(theSelected);
				console.log(this.currentTask);
				})
			})
			
		}
		
	}
}
</script>

<style scoped>
h2 {
	margin-top: 10em;
}
.containerItems{
	margin: auto;
	padding: 1em;
}
a {
	display: block;
	padding: 1em;
	font-size: 1.5em;
}

a:hover{
	cursor: pointer;
	text-decoration: underline;
}
</style>