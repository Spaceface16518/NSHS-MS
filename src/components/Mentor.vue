<template>
  <div class="mentor">
		<ul>
			<li>{{ firstName }} {{lastName}}</li>
			<li v-if="phone"><a :href="'tel:' + phone">{{ phone }}</a></li>
			<li v-if="email"><a :href="'mailto:' + email">{{ email }}</a></li>
		</ul>
	</div> 
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "Mentor",
  props: {
firstName: String,
lastName: String,
phone: String,
email: String
  }
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
