<template>
	<div class="search-block">
		<input placeholder="Search" type="text" v-model="searchedVal" @input="$emit('searchContact', searchedVal)" />
	</div>
</template>

<script>
export default {
	name: "SearchContactsItem",
	data() {
		return {
			searchedVal: null,
		}
	},
}
</script>

<style lang="css" scoped>
.search-block {
	position: relative;
	padding-bottom: 10px;
	margin-bottom: 30px;
}
.search-block::after {
	content: "";
	position: absolute;
	bottom: 0;
	left: 0;
	width: 100%;
	height: 1px;
	background-color: #5a5959;
}
.search-block input {
	position: relative;
	width: 100%;
	border: none;
}
.search-block input:focus {
	outline: none;
}
</style>
