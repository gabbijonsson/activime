<template>
	<header>
		<div class="container">
			<div class="item-1"><img src="../assets/Home.png" alt="Home"></div>
			<div class="item-2"><img src="../assets/Settings.png" alt="esttings"></div>
		</div>
	</header>
</template>

<script>
export default {
	name: 'Header',
	
}
</script>

<style scoped>
.container{
	display: flex;
	background-color: #77c9d4;
	justify-content: space-between;
	align-items: center;
	height: 5em;
	width: 100%;
	left: 0;
	top: 0;	
	position: fixed;
}
img{
	height: 45px;
	width: 45px;
}
.item-1{
	margin-left: 1em;
}
.item-2{
	margin-right: 1em;
}
</style>