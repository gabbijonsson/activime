<template>
  <div class="content">
    <div class="during-sprint--text-container">
      <p
        class="during-sprint--time-spent"
      >Du har jobbat i {{ timeSpentTimer }} <br> sedan din senaste paus.</p>
      <p
        class="during-sprint--time-left"
      >Det är {{ timeLeftTimer }} kvar <br> att jobba med {{ currentTask }}</p>
    </div>
    <EndDay/>
  </div>
</template>

<script>
import EndDay from './EndDay';
import {eventBus} from "../main";
export default {
  name: "DuringSprint",
  data: () => ({
    timeSpentTimer: Number,
    timeLeftTimer: Number,
    currentTask: String
  }),
  components: {
      EndDay
  },
  created(){
    eventBus.$on('currentTask', (currentTask) => {
			this.currentTask = currentTask
			console.log(this.currentTask);
			console.log(currentTask);			
		}),
		console.log('created', this.currentTask);
			console.log('created again', this.currentTask);
  }
};
</script>

<style scoped>
p {
    font-size: 2em;
    margin: 3em 0;
}

.during-sprint--text-container {
  position: absolute;
  top: 50%;
  left: 50%;
  width: 100vw;
  transform: translate(-50%, -50%);
}
</style>