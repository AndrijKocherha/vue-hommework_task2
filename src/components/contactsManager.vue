<template>
	<div>
		<search-contacts-item @searchContact="searchContact" />
		<add-contact-block @add-contact="addNewContact" />
		<contacts-items :contacts-data-list="contactsList" />
	</div>
</template>

<script>
import SearchContactsItem from "./SearchContactsItem.vue"
import AddContactBlock from "./AddContactBlock.vue"
import ContactsItems from "./ContactsItems.vue"
export default {
	name: "ContactsManager",
	components: { SearchContactsItem, AddContactBlock, ContactsItems },
	props: {
		contactsList: {
			type: Array,
			default: () => [],
		},
	},
	methods: {
		addNewContact(newContactData) {
			this.$emit("addContact", newContactData)
		},
		searchContact(searchedVal) {
			this.$emit("searchContact", searchedVal)
		},
	},
}
</script>

<style lang="scss" scoped></style>
