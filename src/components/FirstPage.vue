<template>
	<div class="content">
	<ApiHandler/>
		<div class="firstPageContent">
			<div class="weatherIcon">
				<img src="../assets/img/icon--weather-sunny.svg" alt="weather">
			</div>
			<div class="greeting"> <h1> Välkommen till <br/> ActiveMe-appen, <br/> Användare!</h1> </div>
			<p>{{ startDay }}</p>
			<button @click="handleNextPage">NU KÖR VI!</button>
		</div>
	</div>

</template>

<script>
import ApiHandler from './ApiHandler'

export default {
name: 'FirstPage',
components: {
	ApiHandler,
},
data: () => ({
	greeting: `Välkommen
	till ActiveMe-app, 
	Användare!`,
	startDay: 'Är du redo att påbörja din arbetsdag?',
	
}),
methods: {
	handleNextPage(){
		this.showBeforeSprint = true
		this.$emit('showBfSprint', this.showBeforeSprint)
	}
},
}
</script>

<style scope>
	/* .content{
		position: absolute;
		width: 375px;
		height: 812px;
		left: 0px;
		top: 0px;
		background: url(../assets/BackgroundImg.png);
		mix-blend-mode: overlay;
		filter: blur(10px);
		} */
	html{
		background-color: #bbdadf;
	}
	.content{
		text-align: center;		
	}
	.firstPageContent > button{
		background-color: #77c9d4;
		width: 13em;
		height: 3em;
		border-radius: 20px;
		border: 0em;
		box-shadow: 1px 6px #999;
		font-weight: 600;
		font-size: 18px;
		cursor: pointer;
	}
	.firstPageContent > button:active{
		box-shadow: 0 5px #666;
		transform: translateY(4px);
	}
	h1{
		font-weight: 600;
	}
	p{
		
		font-size: 18px;		
	}
	p:first-child{
		margin-top: 5em;
	}
	.greeting{
		margin-top: 15em;
	}
	.weatherIcon > img{
		position: absolute;
		top: 95px;
		left: 18px;		
		height: 120px;
		width: 120px;
	}
</style>