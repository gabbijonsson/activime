<template>
  <div class="content">
    <ApiHandler />
    <div class="firstpage--bg-img">
      <div class="firstpage--text-container">
        <h1 class="greeting">{{ greeting }}</h1>
        <p>{{ startDay }}</p>
      </div>
      <button class="start-sprint-button">NU KÖR VI!</button>
    </div>
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
  text-align: center;
}

.firstpage--bg-img {
  background: linear-gradient(
      0deg,
      rgba(119, 201, 212, 0.4),
      rgba(119, 201, 212, 0.4)
    ),
    url(../assets/img/background-rocks.jpg);
  mix-blend-mode: overlay;

  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
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