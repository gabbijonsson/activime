<template>

	<div class="content">
		<div class="weatherIcon">
			<img src="../assets/IconSunny.png" alt="weather">
		</div>
		<div class="greeting"> <h1> Välkommen till <br/> ActiveMe-appen, <br/> Användare!</h1> </div>
		<p>{{ startDay }}</p>
		<button>NU KÖR VI!</button>
	</div>

</template>

<script>
export default {
name: 'FirstPage',
components: {

},
data: () => ({
	greeting: `Välkommen
	till ActiveMe-app, 
	Användare!`,
	startDay: 'Är du redo att påbörja din arbetsdag?'
})
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
	.content > button{
		background-color: #77c9d4;
		width: 13em;
		height: 3em;
		border-radius: 20px;
		border: 0em;
		box-shadow: 1px 6px #999;
		font-weight: 600;
		font-size: 18px;
	}
	h1{
		font-weight: 600;
	}
	p{
		margin-top: 5em;
		font-size: 18px;		
	}
	.greeting{
		margin-top: 15em;
	}
	.weatherIcon > img{
		position: absolute;
		top: 95px;
		left: 18px;		
	}
</style>