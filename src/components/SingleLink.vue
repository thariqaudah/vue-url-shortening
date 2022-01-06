<template>
	<div class="single-link container">
		<p class="original-link">{{ link.originalLink }}</p>
		<div class="output">
			<p class="short-link">{{ link.fullShortLink }}</p>
			<button class="btn btn-sm btn-dark" v-if="isCopied">Copied!</button>
			<button class="btn btn-sm" @click="copyLink" v-else>Copy</button>
		</div>
	</div>
</template>

<script>
import { computed, ref } from 'vue';

export default {
	name: 'SingleLink',
	props: ['link', 'copiedLink'],
	setup(props, { emit }) {
		const copied = ref(false);

		const isCopied = computed(
			() => copied.value && props.copiedLink === props.link.fullShortLink
		);

		const copyLink = async () => {
			await navigator.clipboard.writeText(props.link.fullShortLink);
			console.log('Copied!');
			copied.value = true;
			// Emit event to show the parent that something has been copeied to clipboard
			emit('copy');
		};

		return { copyLink, isCopied };
	},
};
</script>

<style lang="scss" scoped>
.single-link {
	display: flex;
	justify-content: space-between;
	align-items: center;
	background-color: #fff;
	padding: 16px 24px;
	border-radius: 5px;

	.original-link {
		color: #35323e;
		font-weight: 500;
	}

	.output {
		display: flex;
		align-items: center;
		gap: 24px;

		.short-link {
			color: #2acfcf;
			font-weight: 500;
		}
	}
}
</style>
