<template>
	<a href="#" class="contact-block">
		<div :style="{ backgroundColor: itemLogoBackgroundColor }" class="contact-block__logo">{{ logoLetters }}</div>
		<div class="contact-block__content">
			<div class="contact-block__name">{{ contactData.first_name }} {{ contactData.last_name }}</div>
			<div class="contact-block__email">{{ contactData.emails[0] }}</div>
		</div>
	</a>
</template>

<script>
export default {
	name: "ContactItem",
	props: {
		contactData: {
			type: Object,
			required: true,
		},
	},
	computed: {
		logoLetters() {
			return this.contactData.first_name[0] + this.contactData.last_name[0]
		},
		itemLogoBackgroundColor() {
			return this.generateRandomColorHex()
		},
	},
	methods: {
		generateRandomColorHex() {
			const randomComponent = () => Math.floor(Math.random() * 256)
			const toHex = (component) => component.toString(16).padStart(2, "0")
			return `#${toHex(randomComponent())}${toHex(randomComponent())}${toHex(randomComponent())}`
		},
	},
}
</script>

<style lang="css" scoped>
.contact-block {
	color: #000;
	text-decoration: none;
	display: flex;
	align-items: center;
	gap: 25px;
	margin-bottom: 40px;
}
.contact-block__logo {
	color: #fff;
	font-size: 20px;
	padding: 10px;
	width: 30px;
	height: 30px;
	border-radius: 50%;
	display: flex;
	align-items: center;
	justify-content: center;
}
.contact-block__content {
	display: grid;
	text-align: start;
	gap: 15px;
}
.contact-block__name {
}
.contact-block__email {
	color: gray;
}
</style>
