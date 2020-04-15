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
    <BeforeSprint v-show="!keepHidden"/>
  </div>
</template>

<script>
import EndDay from './EndDay';
import {eventBus} from "../main";
import BeforeSprint from './BeforeSprint'
export default {
  name: "DuringSprint",
  data: () => ({
    timeSpentTimer: Number,
    timeLeftTimer: Number,
    currentTask: '',
    keepHidden: true
  }),
  components: {
      EndDay,
      BeforeSprint
  },
  methods:{
    theCurrentTask(){
      console.log('current fuction');
      
      this.currentTask = eventBus.$emit('theCurrentTask', this.currentTask)
      console.log('your current one', this.currentTask);
      
    }
  },
  created(){
    console.log('during created');
    
    eventBus.$on('theCurrentTask', (theSelected) => {
      this.currentTask = theSelected;
      console.log(theSelected);
			console.log(this.currentTask);
    })
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