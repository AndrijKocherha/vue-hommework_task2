<template>
	<div>
		<contacts-manager :contacts-list="contacts" @add-contact="addNewContact" @searchContact="searchContact" />
	</div>
</template>

<script>
import { contacts } from "./constants/allContacts"
import ContactsManager from "./components/contactsManager.vue"

export default {
	name: "App",
	components: { ContactsManager },
	data() {
		return {
			contacts,
			allContacts: [],
		}
	},
	created() {
		this.allContacts = JSON.parse(JSON.stringify(this.contacts))
	},
	methods: {
		addNewContact(newContactData) {
			this.contacts.push(newContactData)
		},

		searchContact(searchedVal) {
			if (searchedVal !== "") {
				searchedVal = searchedVal.toLowerCase().trim()
				this.contacts = this.contacts.filter((contact) => {
					let contactFullName = (contact.first_name + contact.last_name).toLocaleLowerCase().trim()
					return contactFullName.includes(searchedVal)
				})
			} else {
				this.contacts = JSON.parse(JSON.stringify(this.allContacts))
			}
		},
	},
}
</script>

<style>
#app {
	font-family: Avenir, Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;
	margin-top: 60px;
}
</style>
