<template>
	<div class="content">
		<activityListDisplay v-if="showActList"/>
		<WorkListDisplay v-else-if="showWorkList"/>

	<div v-else>
		<div class="toDoList">
			<p>ARBETSUPPGIFTER</p>
			<button @click="editWorkList">REDIGERA</button>
		</div>
		<div class="weatherSettings">
			<p class="weatherTitle">VÄDER</p>
			<div class="temp">		<!--Kan stylas bättre -->
				<span class="item-1">Ange lägsta temperatur för <br/> utomhusaktiviteter</span> 
				<span class="item-2"><input @change="emitDegreeValue($event)" class="item-" type="number" id="tempInput" placeholder="°C">
					<span class="item-3">grader</span>
				</span> 
			</div>
			<div class="wheatherIconOnOff">
				<label class="item-1" for="ifIcon">Visa vädersymbol <br/>under arbetspass<br/></label> <input @change="emitCheckboxState($event)" id="ifIcon" type="checkbox" v-model="iconOnOff">
			</div>
		</div>
	</div>
	</div>
</template>

<script>
import ActivityListDisplay from './ActivityListDisplay'
import WorkListDisplay from './WorkListDisplay'

export default {
	name: 'SettingsPage',
	components:{
		ActivityListDisplay,
		WorkListDisplay,
	},
	data: () => ({
		activityList: [],
		toDoList: [],
		iconOnOff: Boolean,  //! Boolean för att visa eller inte väder icon
		degreeValue: Number,
		showActList: false,
		showWorkList: false,
		showSettings: true,
	}),
	computed: {

	},
	props: {

	},
	methods:{
		emitCheckboxState(state){			//! Emitar valet av vädericon. måste kopplas ihop med väder-komponenten!
			console.log('state changed!', state.target.checked);
			this.iconOnOff = state.target.checked;
			localStorage.setItem('weatherIconState', JSON.stringify(this.iconOnOff))			
			this.$emit('checkboxOnOff', this.iconOnOff)
		},
		emitDegreeValue(Value){		//! Emitar valet av gradantal. måste kopplas ihop med väder-komponenten!
			this.degreeValue = Value.target.valueAsNumber;	//! Här lägger sig det inskrivna gradantalet!
			console.log(this.degreeValue);
			localStorage.setItem('userDegrees', JSON.stringify(this.degreeValue))
			this.$emit('userDegrees', this.degreeValue)
		},
		editActList(){
			this.showActList = true
			this.showWorkList = false
			this.showSettings = false
		},
		editWorkList(){
			this.showActList = false
			this.showWorkList = true
			this.showSettings = false
		},
	},
	mounted(){
		console.log('Settings mounted!');
		if(localStorage.getItem('weatherIconState')){
			this.iconOnOff = JSON.parse(localStorage.getItem('weatherIconState'))
			this.$emit('checkboxOnOff', this.iconOnOff)
		}else{
			this.iconOnOff = true
			localStorage.setItem('weatherIconState', JSON.stringify(this.iconOnOff))
			this.$emit('checkboxOnOff', this.iconOnOff)
		}
		if(localStorage.getItem('userDegrees')){
			this.degreeValue = JSON.parse(localStorage.getItem('userDegrees'))
			this.$emit('userDegrees', this.degreeValue)
		}
	}
}
</script>

<style scoped>
.weatherSettings {
	display: grid;
	grid-template-columns: 1fr 1fr;
	max-width: 80%;
	margin: auto;
}
.weatherTitle {
	grid-column: 1 / 3;
}

input {
	margin-top: 1em;
}

.toDoList > p, .weatherSettings > p{
	margin-top: 1em;
}
button{
	background-color: #a5a5af;
	margin: 1em 2em 2em 2em;
	width: 10em;
	height: 2.5em;
	border-radius: 20px;
	border: 0em;
	box-shadow: 1px 6px #999;
	font-size: 18px;
	cursor: pointer;
}
button:active{
	box-shadow: 0 5px #666;
	transform: translateY(4px);
}

</style>