<template>
	<div>
		<contact-item v-for="(contact, indx) in contactsDataList" :contact-data="contact" :key="indx" />
	</div>
</template>

<script>
import ContactItem from "./ContactItem.vue"
export default {
	name: "ContactsItems",
	components: { ContactItem },
	props: {
		contactsDataList: {
			type: Array,
			default: () => [],
		},
	},
}
</script>

<style lang="scss" scoped></style>
