<template>
	<div id="app">
		<VinEolMatchForm />
		<hr />
		<RollOverSettings />
	</div>
</template>

<script>
import VinEolMatchForm from "@/components/VinEolMatchForm.vue";
import RollOverSettings from "@/components/RollOverSettings.vue";

export default {
	name: "app",
	components: {
		VinEolMatchForm,
		RollOverSettings,
	},
	data() {
		return {};
	},
};
</script>

<style>
#app {
	/* font-family: Avenir, Helvetica, Arial, sans-serif; */
	box-sizing: border-box;
}
button {
	background-color: gold;
}
</style>
