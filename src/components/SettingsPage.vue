<template>
	<div class="content">
		<activityListDisplay v-if="showActList"/>
		<WorkListDisplay v-else-if="showWorkList"/>

	<div v-else>
		<div class="activityList">
			<P>AKTIVITETSLISTA</P>
			<button @click="editActList">REDIGERA</button>
		</div>
		<div class="toDoList">
			<p>ARBETSUPPGIFTER</p>
			<button @click="editWorkList">REDIGERA</button>
		</div>
		<div class="weatherSettings">
			<p>VÄDER</p>
			<div class="temp">		<!--Kan stylas bättre -->
				<span class="item-1">Ange lägsta temperatur för <br/> utomhusaktiviteter</span> <span class="item-2"><input @change="emitDegreeValue($event)" class="item-" type="number" id="tempInput" placeholder="°C"><span class="item-3">grader</span></span> 
			</div>
			<div class="wheatherIconOnOff">
				<label for="ifIcon">Visa vädersymbol under arbetspass</label> <input @change="emitCheckboxState($event)" id="ifIcon" type="checkbox" v-model="iconOnOff">
				{{iconOnOff}}			
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
.activityList{
	margin-top: 8em;
}
.temp{
	display: flex;
	justify-content: space-evenly;
	align-content: center;
	margin-top: 2em;
}
.item-1{

}
.item-2{
	display: flex;
	
}
.item-{
	width: 3em;
	height: 1.5em;
	margin-right: 1em;
}
.item-3{
	
}
.wheatherIconOnOff{
	margin-top: 2em;
	display: flex;
	justify-content: space-evenly;
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