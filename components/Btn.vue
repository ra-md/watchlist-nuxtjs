<template>
	<button
		:disabled="disabled"
		:class="isSpecial"
		class="font-medium text-sm py-2 px-4 focus:outline-none"
	>
		<slot />
	</button>
</template>

<script>
export default {
	name: 'Btn',
	props: {
		disabled: {
			type: Boolean,
			default: () => false
		},
		special: {
			type: Boolean,
			default: () => false
		},
		active: {
			type: Boolean,
			default: () => false
		},
		bg: {
			type: String,
			default: 'bg-primary'
		},
		textColor: {
			type: String,
			default: 'text-white'
		},
		width: {
			type: String,
			default: 'width-auto'
		},
		rounded: {
			type: String,
			default: 'rounded'
		}
	},
	computed: {
		isSpecial() {
			if (this.special) {
				return `rounded-full border-2 border-primary hover:shadow-outline ${this.active ? 'bg-primary text-white' : 'bg-none text-primary'}`;
			} else {
				return `${this.bg} ${this.textColor} ${this.width} ${this.rounded} hover:bg-opacity-75 focus:shadow-outline`;
			}
		}
	}
};
</script>

<style scoped>
	button:disabled {
		@apply bg-opacity-25 cursor-not-allowed;
	}
</style>
