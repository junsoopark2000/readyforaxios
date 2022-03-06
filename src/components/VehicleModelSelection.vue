<template>
	<div class="vehicle-model-selection">
		<label>Vehicle Model</label>
		<select v-model="selected" @change="myUpdate">
			<option value="">select a model</option>
			<option v-for="(vehicleModel, idx) in vehicleModels" :key="idx">
				{{ vehicleModel }}
			</option>
		</select>
	</div>
</template>

<script>
export default {
	name: "VehicleModelSelection",

	data() {
		return {
			selected: "",
			vehicleModels: ["X1222", "H2X6", "M2345"],
		};
	},
	methods: {
		myUpdate() {
			this.$emit("model-selected", this.selected);
		},
	},
};
</script>

<style></style>
