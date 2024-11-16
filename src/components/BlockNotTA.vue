<script>
export default {
	props: {
		id: Number,
		title: String,
		post: String,

	},
	emits: ['changePost'],
	data() {
		return {
			inp: '',
			isEdit: false,
		}
	},
	methods: {
		change: function () {
			this.$emit('changePost', this.id, this.inp)
		},
		change_isEdit: function () {
			if (!this.isEdit) {
				this.inp = this.post
			} else {
				this.change()
			}
			this.isEdit = !this.isEdit
		}
	},


}
</script>

<template>
	<p v-if="!isEdit" @click="change_isEdit">{{ post }}</p>
	<div v-else>
		<textarea v-model="inp">
		</textarea>
		<button @click="change_isEdit">сохранить</button>
	</div>
</template>
