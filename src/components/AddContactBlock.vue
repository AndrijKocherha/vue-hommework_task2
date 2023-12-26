<template>
	<div class="add-contact">
		<button @click="showAddContactForm" class="add-contact__btn">Add new Contact</button>
		<div v-if="isAddContact" class="add-contact__form">
			<form action="">
				<div class="add-contact__block">
					<label for="01"> E-mail </label>
					<input v-model="newEmail" id="01" type="email" />
				</div>
				<div class="add-contact__block">
					<label for="02"> First name </label>
					<input v-model="newFirstName" id="02" type="text" />
				</div>
				<div class="add-contact__block">
					<label for="03"> Last name </label>
					<input v-model="newLastName" id="03" type="text" />
				</div>
				<button type="button" @click="addContact" class="add-contact__create">Add</button>
			</form>
		</div>
	</div>
</template>

<script>
export default {
	name: "AddContactBlock",
	data() {
		return {
			newEmail: null,
			newFirstName: null,
			newLastName: null,
			isAddContact: false,
		}
	},
	methods: {
		addContact() {
			if (this.newEmail && this.newFirstName && this.newLastName) {
				const newContactData = {
					emails: [this.newEmail],
					first_name: this.newFirstName,
					last_name: this.newLastName,
				}
				this.$emit("addContact", newContactData)
			}
		},
		showAddContactForm() {
			this.isAddContact = !this.isAddContact
		},
	},
}
</script>

<style lang="css" scoped>
.add-contact {
	margin-bottom: 40px;
}
.add-contact__btn {
	color: green;
	background-color: transparent;
	border: none;
	display: flex;
	align-items: center;
	gap: 20px;
	cursor: pointer;
	margin-bottom: 30px;
}
.add-contact__btn::before {
	content: "+";
	display: flex;
	align-items: center;
	justify-content: center;
	flex: 0 0 30px;
	width: 30px;
	height: 30px;
	font-size: 25px;
	border-radius: 50%;
	border: 1px dotted green;
}
.add-contact__form form {
	text-align: start;
	display: grid;
	justify-content: start;
	gap: 20px;
}
.add-contact__block {
}
.add-contact__create {
}
</style>
