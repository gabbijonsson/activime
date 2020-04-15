<template>
  <div class="content">
    <div class="ending-sprint--text-container">
        <h1 class="ending-sprint--header">Tiden är ute!</h1>
        <p class="ending-sprint--pause-activity-suggestion">
            Dags för en välförtjänt paus. Varför inte {{ activitySuggestion }}?
        </p>
        <p class="ending-sprint--verify-taskcompletion">
            Blev du färdig med {{ currentTask.title }}?
        </p>
        <button @click="endTask">JA</button>
        <button>NEJ</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "EndingSprint",
  data: () => ({
      activityList: [
        'en kaffepaus',
        'en promenad',
        'ett stretchpass',
        'en vilopaus',
        'läsa ett kapitel i din bok'
    ]
  }),
  computed: {
      activitySuggestion: function (){
          return this.activityList[Math.floor(Math.random() * this.activityList.length)]
      }
  },
  methods: {
    endTask: function() {
        let finishedTasks = JSON.parse(localStorage.getItem('finishedTasks'));
        if(!finishedTasks) {
            finishedTasks = [];
        }
        finishedTasks.push(this.currentTask);
        localStorage.setItem('finishedTasks', JSON.stringify(finishedTasks));

        let worklist = JSON.parse(localStorage.getItem('worklist'));
        let index = worklist.findIndex((workTask) => workTask.title === this.currentTask);
        worklist.splice(index, 1);
        localStorage.setItem('worklist', JSON.stringify(worklist));
    }
  },
  created(){
      this.currentTask = JSON.parse(localStorage.getItem('currentTask'))
  }
};
</script>

<style scope>
p {
  font-size: 2em;
  margin: 3em 0;
}
.ending-sprint--text-container {
  position: absolute;
  top: 50%;
  left: 50%;
  width: 100vw;
  transform: translate(-50%, -50%);
}
button {
  background-color: #77c9d4;
  width: 10em;
  height: 3em;
  border-radius: 20px;
  border: 0em;
  box-shadow: 1px 6px #999;
  font-weight: 600;
  font-size: 18px;
  cursor: pointer;
  margin: 0.5em;
}
</style>