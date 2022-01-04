<template>
	<div class="shorten-form container">
		<form class="form">
			<input type="text" placeholder="Shorten a link from here..." />
			<button type="submit" class="btn">Shorten It!</button>
		</form>
	</div>
</template>

<script>
export default {
	name: 'ShortenForm',
};
</script>

<style lang="scss" scoped>
.shorten-form {
	background-color: #3b3054;
	padding: 48px;
	border-radius: 9px;
	background-image: url('../assets/bg-shorten-desktop.svg');
	background-repeat: no-repeat;
	background-size: cover;
	transform: translateY(50%);

	.form {
		display: flex;
		gap: 24px;

		input {
			flex: 1;
			border: none;
			padding: 0 24px;
			font-family: inherit;
			font-size: inherit;
			color: #35323e;
			border-radius: 7px;
		}
	}
}
</style>
