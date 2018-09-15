<template>
	<div id="app">
		<loading
			:loading-radius-val="loadingRadius"
			:dot-radius-val="dotRadius"
			:dot-color-val="dotColor"
			:dot-nums="dotNums"
		></loading>
	</div>
</template>

<script>
import Loading from "./components/Loading";

export default {
	name: 'App',
	components: {
		Loading
	},
	data() {
		return {
			loadingRadius: 168,
			dotRadius: 20,
			dotColor: '#ff3366',
			dotNums: 8
		};
	}
}
</script>

<style lang="scss">
body {
	width: 100vw;
	height: 100vh;
	display: flex;
	justify-content: center;
	align-items: center;
}
#app {
	width: 100vw;
	height: 100vh;
	display: flex;
	justify-content: center;
	align-items: center;
	
	> div {
		margin: 0 2rem;
	}
}
</style>
