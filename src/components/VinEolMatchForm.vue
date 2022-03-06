<template>
	<div class="vin-eol-match-form">
		<!-- EOL 동작확인 -->
		<form @submit.prevent>
			<BaseInput label="EOL" v-model="eol" type="text" />
			<button type="submit" @click="EolOperationCheckRequest">동작확인</button>
		</form>
		<hr />

		<!-- EOL - VIN 매칭 -->
		<form @submit.prevent>
			<BaseInput label="EOL" v-model="eol" type="text" />
			<BaseInput label="VIN" v-model="vin" type="text" />
			<VehicleModelSelection @model-selected="modelSelected" />
			<button type="submit" @click="matchRequest">매칭</button>
		</form>
	</div>
</template>

<script>
import BaseInput from "@/components/BaseInput.vue";
import VehicleModelSelection from "@/components/VehicleModelSelection.vue";

export default {
	name: "VinEolMatchForm",
	components: {
		BaseInput,
		VehicleModelSelection,
	},
	data() {
		return {
			eol: "",
			vin: "",
			model: "",
		};
	},
	methods: {
		EolOperationCheckRequest() {
			console.log(this.eol, ":eol operation check in-progress");
			if (this.eol) {
				// on success
				// this.$emit("eol-verified");
				// on  failure
			}
		},
		matchRequest() {
			if (this.eol && this.vin && this.model) {
				console.log(`matching...${this.eol}, ${this.vin}, ${this.model}`);
			}
		},
		modelSelected(value) {
			this.model = value;
		},
	},
};
</script>

<style scopoed></style>
