<template>
	<footer class="footer">
		<div class="container">
			<div class="item-1">© 2020 ActiviMe</div>
			<div class="item-2"><a href="https://twitter.com/pomodorotech" target="blank"><img src="../assets/img/icon--social-twitter.svg" alt="Twitter Icon"></a></div>
			<div class="item-3"><a href="https://www.facebook.com/PomodoroPPB" target="blank"><img src="../assets/img/icon--social-facebook.svg" alt="Facebook icon"></a></div>
			<div class="item-4"><a href="https://github.com/gabbijonsson/activime" target="blank"><img src="../assets/img/icon--social-git.svg" alt="GitHub Icon"></a></div>			
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