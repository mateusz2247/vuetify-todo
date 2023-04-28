<template>
	<v-app id="inspire">
		<v-navigation-drawer v-model="drawer" app>
			<v-list>
				<v-list-item
					prepend-icon="mdi-format-list-checks"
					title="Home"
					value="home"
					to="/"></v-list-item>

				<v-list-item
					prepend-icon="mdi-trash-can"
					title="Removed tasks"
					value="Removed tasks"
					to="/Removed"></v-list-item>	

				<v-list-item
					prepend-icon="mdi-forum"
					title="About"
					value="about"
					to="/about"></v-list-item>

				


			</v-list>
			
		</v-navigation-drawer>
		//
		<v-app-bar
			
			color="teal-darken-4"
			>
			<template v-slot:image>
				<v-img
					gradient="to top right, rgba(19,84,122,.8), rgba(128,208,199,.8)"></v-img>
			</template>

			<template v-slot:prepend>
				<v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>
			</template>

			<v-app-bar-title>ToDo app</v-app-bar-title>

		</v-app-bar>

		<v-main>
			<router-view></router-view>
		</v-main>
	</v-app>
</template>

<script>
export default {
	data: () => ({ drawer: null }),
};
</script>
