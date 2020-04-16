<template>
  <div class="content">
    <!-- <SettingsPage v-if="showSettings"/> -->
    <div class="firstpage--bgimg-container"></div>
    <div class="firstpage--text-container">
      <h1 class="greeting">{{ greeting }}</h1>
      <p>{{ startDay }}</p>
      <button @click="handleNextPage" class="start-sprint-button">NU KÖR VI!</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "FirstPage",
  data: () => ({
    greeting: `Välkommen
	till ActiviMe!`,
	startDay: "Är du redo att påbörja din arbetsdag?",
	showBeforeSprint: Boolean,
  }),
  methods: {
	handleNextPage(){
		this.showBeforeSprint = true
		this.$emit('showBfSprint', this.showBeforeSprint)
	}
},
};
</script>

<style scope>
html {
  background-color: #bbdadf;
}
h1 {
  font-weight: 600;
}
p {
  font-size: 18px;
}
.content {
  position: relative;
  height: 100%;
  width: 100%;
  text-align: center;
}
.firstpage--bgimg-container {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  z-index: -1;
  background: linear-gradient(
      0deg,
      rgba(119, 201, 212, 0.4),
      rgba(119, 201, 212, 0.4)
    ),
    url(../assets/img/background-rocks.jpg) no-repeat center center fixed;
  background-size: auto;
  filter: blur(5px);
}
.firstpage--text-container {
  position: absolute;
  top: 50%;
  left: 50%;
  width: 100vw;
  transform: translate(-50%, -50%);
  background-color: rgba(119, 201, 212, 0.7);
}
.start-sprint-button {
  background-color: #77c9d4;
  width: 13em;
  height: 3em;
  border-radius: 20px;
  border: 0em;
  box-shadow: 1px 6px #999;
  font-weight: 600;
  font-size: 18px;
  cursor: pointer;
  margin-bottom: 2em;
}
.start-sprint-button:active {
  box-shadow: 0 5px #666;
  transform: translateY(4px);
}
</style>