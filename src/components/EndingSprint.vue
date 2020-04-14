<template>
    <div class="content">
        <div class="ending-sprint--text-container">
            <p class="ending-sprint--time-spent">Tiden är ute! <br><br>
            Dags för en paus,<br>Förslag:<br>{{ förslag }}</p>
            <p class="">
                blev du färdig med<br> {{ currentTask }} ? <br>
                <button id="yesIdid" v-on:click="deleteTask">JA</button>
                <button id="noIdidnt">NEJ</button>
            </p>
        </div>
        <EndDay/>
    </div>
</template>

<script>
//import ApiHandler from "./ApiHandler";
import EndDay from "./EndDay";
//import aktivitetsLista from "";
//import arbetsUppgift from "";

export default {
  name: "EndingSprint",
  components: {
      EndDay
    //ApiHandler,
   //arbetsUppgift // Tänker ni att man skall radera arbetsuppgiften om man klickar JA på knappen?
  },
  data: () => ({
    //förslagslista: "aktivitetslista",
    //currentTask: "???"
  }),
  methods: {
		deleteTask: function(event) {
			this.currentTask = 'delete';  // this refererar till data-objektet
		}
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
    font-family: Montserrat;
    font-style: normal;
    font-weight: normal;
    font-size: 18px;
    line-height: 22px;
    display: inline;
    align-items: center;
    text-align: center;
    color: #000000;
    padding: 0.3em 3.2em;
    margin: 2em 0.9em;
}
#yesIdid {
    background: #77C9D4;
    box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
    border-radius: 16px;
}
#noIdidnt {
    background: #A5A5AF;
    box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
    border-radius: 16px;
}
</style>