<template>
  <div class="content">
	  		<!-- <SettingsPage v-if="showSettings"/> -->
    <ApiHandler />
	<div class="firstpage--bgimg-container"></div>
    <div class="firstpage--text-container">
      <h1 class="greeting">{{ greeting }}</h1>
      <p>{{ startDay }}</p>
    </div>
    <button class="start-sprint-button">NU KÖR VI!</button>
  </div>
</template>

<script>
import ApiHandler from "./ApiHandler";
export default {
  name: "FirstPage",
  components: {
    ApiHandler
  },
  data: () => ({
    greeting: `Välkommen
	till ActiviMe,
	Användare!`,
    startDay: "Är du redo att påbörja din arbetsdag?"
  })
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
  margin-top: 5em;
  font-size: 18px;
}

.content {
	position: relative;
	height: 100vh;
	width: 100vw;
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
}
.greeting {
  margin-top: 3em;
}
</style>