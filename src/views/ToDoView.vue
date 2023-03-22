<template>
	<div class="home pa-6">
		<v-text-field
			v-model="newTaskTitle"
			@click:append-inner="addTask"
			@keyup.enter="addTask"
			class="pa-3"
			variant="underlined"
			label="Wpisz zadanie do wykonania"
			append-inner-icon="mdi-plus"
			hide-details
			clearable></v-text-field>
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
	</div>
</template>

<script setup>
import { reactive, ref } from "vue";

let newTask;

let tasks = reactive([

]);
let newTaskTitle = ref("");
function addTask() {
	let newTask = {
		id: Date.now(),
		title: newTaskTitle.value,
		done: false,
	};
	tasks.push(newTask);
	newTaskTitle.value=''
}

function doneTask(id) {
	let task = this.tasks.filter((task) => task.id === id)[0];
	console.log(task);
	task.done = !task.done;
}

function deleteTask(id) {
	const pos = this.tasks.map((e) => e.id).indexOf(id);
	console.log(pos);
	this.tasks.splice(pos, 1);
}
</script>
