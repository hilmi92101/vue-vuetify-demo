<template>
	<div class="home">
		<v-list flat class="pt-0">
		
			<div v-for="task in tasks" :key="task.id">
				<v-list-item 
					@click="doneTask(task.id)"
					:class="{ 'blue lighten-4' : task.done }"
				>
					<template v-slot:default>
						<v-list-item-action>
							<v-checkbox 
								:input-value="task.done"
							> 
							</v-checkbox>
						</v-list-item-action>

						<v-list-item-content>
							<v-list-item-title
								:class="{ 'text-decoration-line-through' : task.done }"
							>{{
								task.title
							}}</v-list-item-title>
						</v-list-item-content>
					</template>
				</v-list-item>
				<v-divider></v-divider>
			</div>
		</v-list>
	</div>
</template>

<script>
	export default {
		name: "Home",
		data() {
			return {
				tasks: [
					{
						id: 1,
						title: "Wake up",
						done: true,
					},
					{
						id: 2,
						title: "Take a shower",
						done: false,
					},
					{
						id: 3,
						title: "Make Breakfast",
						done: false,
					},
				],
			};
		},

		methods: {

			doneTask(id){

				let task = this.tasks.filter(task => task.id == id)[0];
				task.done = !task.done;
			},
		},
	};
</script>
