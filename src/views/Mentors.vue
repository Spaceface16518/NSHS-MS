<template>
  <div class="mentors">
    <h1>Mentors</h1>
		
		<Query :query="allMentors" v-slot="result">
				<h3 v-if="result.isFetching">Loading...</h3>
				<h3 v-if="result.error">Error: {{ result.error }}</h3>
			<ul v-if="result.isDone">
				<li v-for="mentor in result.data['allMentors'].data" v-bind:key="mentor._id">
				<Mentor :firstName="mentor.firstName" :lastName="mentor.lastName" :phone="mentor.phone" :email="mentor.email" />
				</li>
			</ul>
		</Query>
  </div>
</template>

<script>
import { defineComponent } from "vue";
import Mentor from "../components/Mentor";
import { Query } from "villus";

export default defineComponent({
  name: "Mentors",
	components: {Mentor, Query},
	data() {
		return {
			allMentors: `{
				allMentors {
					data {
						_id
						firstName
						lastName
						phone
						email
					}
				}
			}`
		}
	},
});
</script>

<style>
ul {
	list-style-type: none;
	padding: 0;
	margin: 0;
}
</style>
