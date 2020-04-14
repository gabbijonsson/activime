<template>
	<header>
		<div class="container">
			<div class="item-1" @click="handleHome"><img src="../assets/img/icon--navigation-home.svg" alt="Hem-ikon"></div>
			<div class="item-2" @click="handleSettings"><img src="../assets/img/icon--navigation-settings.svg" alt="Inställnings-ikon"></div>
		</div>
	</header>
</template>

<script>
export default {
	name: 'Header',
	data: () => ({
		showSettings: false,
		showFirstPage: true,
	}),
	methods:{
		handleHome(){
			this.showSettings = false;
			this.showFirstPage = true;
			this.$emit('showHome', {'settings': this.showSettings, 'firstpage': this.showFirstPage})
		},
		handleSettings(){
			this.showSettings = true;
			this.showFirstPage = false;
			this.$emit('showsettings', {'settings': this.showSettings, 'firstpage': this.showFirstPage})
		},
	}
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
	cursor: pointer;
}
.item-1{
	margin-left: 1em;
	cursor: pointer;
}
.item-2{
	margin-right: 1em;
	cursor: pointer;
}
</style>