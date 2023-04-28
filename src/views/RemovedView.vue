<template>
    <v-list select-strategy="classic" class="pt-0">
			<div v-for="task in tasks" :key="task.id">
				<v-list-item :class="{ 'bg-green': task.done }">
					<template v-slot:prepend>
						<v-list-item-action>
							<v-checkbox-btn
								@click="doneTask(task.id)"
								:model-value="task.done"></v-checkbox-btn>
						</v-list-item-action>
						<v-list-item-title
							:class="{ 'text-decoration-line-through': task.done }"
							>{{ task.title }}</v-list-item-title
						>

						<v-list-item-action>
							<v-btn right
								@click="deleteTask(task.id)"
								color="red"
								icon="mdi-delete"
								variant="text"></v-btn>
						</v-list-item-action>
					</template>
				</v-list-item>
				<v-divider></v-divider>
			</div>
		</v-list>
</template>