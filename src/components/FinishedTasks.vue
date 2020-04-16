<template>
	<div class="content">
		<div class="container-finishedlist"
		v-for="task in doneTasks" :key="task.id">
			{{ task.title }} 
		</div>
		{{errormsg}}
	</div>
</template>

<script>
export default {
	name: 'FinishedTasks',
	data: () => ({
		doneTasks: [],
		worklist: [],
		errormsg: '',
	}),
	methods: {
		showFinished(){
			this.doneTasks = this.worklist.filter(function(task){
				return task.finished == true;
			});
			console.log('Tasks that are avaliable', this.doneTasks);			
			
		},
		tasksThatAreDone(){
			if(localStorage.getItem('worklist')){
				this.worklist = JSON.parse(localStorage.getItem('worklist'));
				this.showFinished()
			}else
			this.errormsg = 'There are no finished tasks!'
		}
	},
	
	mounted(){
		this.tasksThatAreDone()
	}
}
</script>

<style>

</style>