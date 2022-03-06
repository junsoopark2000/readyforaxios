<template>
	<div class="base-input">
		<label>
			<span>{{ label }}</span>
			<input :type="type" :value="value" @input="update" />
		</label>
	</div>
</template>

<script>
export default {
	name: "BaseInput",
	props: {
		label: {
			type: String,
		},
		type: {
			type: String,
			required: true,
			default: "text",
		},
		value: {
			type: String,
		},
	},
	data() {
		return {};
	},
	methods: {
		update(evt) {
			// console.log("a character is enterd", evt.target.value);
			this.$emit("input", evt.target.value);
		},
	},
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.base-input span {
	display: block;
	margin: 12px, auto;
}
.base-input input {
	margin-bottom: 12px;
}
</style>
