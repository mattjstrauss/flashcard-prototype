<template>
	
	<div class="ui basic content center aligned segment">

		<button class="ui basic button icon" v-show="!isCreating" v-on:click="openForm">

			<i class="plus icon">
		
			</i>

		</button>

		<div class="ui centered card" v-show="isCreating">
			<div class="content">
				<div class="ui form">
					<div class="field">
						<label for="">Title</label>
						<input type="text" v-model="titleText">
					</div>
					<div class="field">
						<label for="">Description</label>
						<input type="text" v-model="descriptionText">
					</div>
					<div class="ui two button attached buttons">
						<button class="ui basic green button" v-on:click="saveQuiz">Save</button>
						<button class="ui basic red button" v-on:click="closeForm">Cancel</button>
					</div>
				</div>
			</div>
		</div>

	</div>

</template>

<script>
	
export default {
	data() {
		return {
			isCreating: false,
			titleText: "",
			descriptionText: "",
		}
	},
	methods: {
		openForm(){
			this.isCreating = true;
		},
		closeForm(){
			this.isCreating = false;
		},
		saveQuiz(){
			this.$emit('create-quiz', {
				title: this.titleText,
				description: this.descriptionText
			});
			this.titleText = "";
			this.descriptionText = "";
			this.isCreating = false;
		}
	}
}

</script>

<style scoped>

</style>