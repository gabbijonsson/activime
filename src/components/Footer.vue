<template>
	<footer class="footer">
		<div class="container">
			<div class="item-1">© 2020 ActiviMe</div>
			<div class="item-2"><img src="../assets/TwitterIcon.png" alt="Twitter Icon"></div>
			<div class="item-3"><img src="../assets/FacebookIcon.png" alt="Facebook icon"></div>
			<div class="item-4"><img src="../assets/Giticon.png" alt="GitHub"></div>			
		</div>
	</footer>
</template>

<script>
export default {
	name: 'Footer'
}
</script>

<style scoped>
.container{
	display: flex;
	background-color: #77c9d4;
	align-items: center;
	height: 5em;
	position: fixed;
	bottom: 0;
	width: 100vw;
	left: 0;
}
img{
	height: 45px;
	width: 45px;
}
.item-1{
	margin-left: 1em;
	flex-grow: 1;
	font-size: 18px;
}
.item-2, .item-3, .item-4{
	margin-right: 1em;
}
</style>