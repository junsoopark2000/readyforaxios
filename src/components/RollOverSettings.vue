<template>
	<div class="roll-over-settings">
		<form @submit.prevent>
			<BaseInput label="VIN" v-model="vin" type="text" />
			<button type="submit" @click="rollOverSettings">설정</button>
		</form>

		<p v-show="requests.length > 0">요청 | 처리 현황</p>
		<p v-for="(request, idx) in requests" :key="idx + 'r'">
			{{ request.vin }} : {{ request.status }}
		</p>
		<!-- <p>-- 미완료 현황 --</p>
		<p v-for="(pendingRequest, idx) in pendingRequests" :key="idx + 'p'">
			
			{{ pendingRequest.vin }} : {{ pendingRequest.status }}
		</p> -->
	</div>
</template>

<script>
import BaseInput from "@/components/BaseInput.vue";

export default {
	name: "RorForm",
	components: {
		BaseInput,
	},
	data() {
		return {
			vin: "",
			requests: [],
		};
	},
	methods: {
		rollOverSettings() {
			if (this.vin) {
				this.requests.push({ vin: this.vin, status: "IN-PROGRESS" });
				console.log(this.vin, ": roll-over setting in-process...");

				// success, USE Retured VIN, not this.vin
				setTimeout(() => {
					this.statusUpdate(this.vin);
				}, 3000);

				// failure
			}
		},
		statusUpdate(vin) {
			for (let i = 0; i < this.requests.length; i++) {
				if (this.requests[i].vin === vin) {
					this.requests[i].status = "DONE";
				}
			}
		},
	},
	computed: {
		pendingRequests() {
			return this.requests.filter(function (request) {
				return request.status === "IN-PROGRESS";
			});
		},
	},
};
</script>

<style></style>
