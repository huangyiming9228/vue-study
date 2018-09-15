<template>
	<div id="app">
		<loading
			:loading-radius-val="loadingRadius"
			:dot-radius-val="dotRadius"
			:dot-color-val="dotColor"
			:dot-nums="dotNums"
		></loading>
		<div class="control">
			<div class="control-form">
				<label for="dotNums">圆点个数:</label>
				<input type="number" step="1" min="8" max="20" id="dotNums" v-model.number="dotNums"   />
			</div>
			<div class="control-form">
				<label for="loadingRadius">容器半径:</label>
				<input type="range" min="50" max="200" step="1" id="loadingRadius" v-model.number="loadingRadius"  />
			</div>
			<div class="control-form">
				<label for="dotRadius">圆点半径:</label>
				<input type="range" min="8" max="30" step="1" id="dotRadius" v-model.number="dotRadius"  />
			</div>
			<div class="control-form">
				<label for="dotColor">圆点颜色:</label>
				<input type="color" v-model="dotColor" id="dotColor"  />
			</div>
		</div>
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
.control-form {
  margin: 10px 0;
}
</style>
