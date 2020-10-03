<template>
  <div id="nav">
    <router-link to="/">Home</router-link> |
    <router-link to="/mentors">Mentor Directory</router-link>
  </div>
  <router-view />
</template>

<script>
	import { defineComponent } from "vue";
	import { useClient, defaultPlugins } from "villus";
	export default defineComponent({
		name: "App",
		setup() {
			function authPlugin({opContext}){opContext.headers.Authorization = "Bearer fnAD3LFuxIACAjaUywlkAiWKbquJvYOmK3x1JTN_" }
			useClient({
				url: 'https://graphql.fauna.com/graphql',
				use: [authPlugin, ...defaultPlugins()]
			})
		}
	})
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
