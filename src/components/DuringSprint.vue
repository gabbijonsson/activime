<template>
  <div class="content">
    <div class="during-sprint--text-container">
      <p
        class="during-sprint--time-spent"
      >Du har jobbat i {{ timeSpentTimer }} <br> minuter sedan din senaste paus.</p>
      <p
        class="during-sprint--time-left"
      >Det är {{ timeLeftTimer }} minuter kvar <br> att jobba med {{ currentTask.title }}</p>
    </div>
    <BeforeSprint v-show="!keepHidden"/>
  </div>
</template>

<script>

import BeforeSprint from './BeforeSprint'
export default {
  name: "DuringSprint",
  data: () => ({
    currentTask: '',
    timeSpentTimer: 0,
    timeLeftTimer: 25,
    timer: {},
    keepHidden: true
  }),
  components: {
      BeforeSprint
  },
  created(){

    this.timer = setInterval(() => {
      this.timeSpentTimer++;
      this.timeLeftTimer--;
      if (this.timeLeftTimer <= 0) {
        clearInterval(this.timer);
      }
    }, 500); //time flies
    
    console.log('during created');
    
    this.currentTask = JSON.parse(localStorage.getItem('currentTask'));
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
  top: 25%;
  left: 50%;
  width: 100vw;
  transform: translate(-50%, -50%);
}
</style>