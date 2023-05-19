<template>
	<div id="grid-item-1">
		<div id="todo-title-container">
			<h2>Lista todo</h2>
			<h2>Wykonane: {{counter}}</h2>
		</div>
		<ul>
			<li v-for="(todo, index) in todos" :key="index">
				<input id="svgCheck" type="checkbox" v-model="todo.done"/>
				<span :class="{ done: todo.done }">{{ todo.text }}</span>
				<label for="svgCheck"></label>
			</li>
		</ul>
		<form @submit.prevent="addTodo">
			<input type="text" placeholder="Dodaj nowy element checklisty" v-model="newTodo" />
			<button type="submit">+</button>
		</form>
	</div>
</template>

<script>
export default {
	data() {
		return {
			counter: 0,
			todos: [
				{ text: 'Lorem ipsum dolor sit amet, consectetur', done: false },
				{ text: 'Sed du eiusmod tempor incididunt', done: true },
				{ text: 'Labore et dolore magna aliqua', done: false },
				{ text: 'Sed ut perspiciatis unde omnis iste natus', done: false },
				{ text: 'Minima veniam, quis nostrum exercitationem', done: false },
			],
			newTodo: '',
		};
	},

	methods: {
		addTodo() {
			if (this.newTodo.trim()) {
				this.todos.push({ text: this.newTodo, done: false });
				this.newTodo = '';
			}
		},
		count() {
			this.counter = 0;
			this.todos.forEach(todo => {
				if(todo.done === true){
					this.counter += 1;
				}
			});
			console.log(this.counter)
			return this.counter
		},
	},

	mounted() { this.count() },
	beforeUpdate() { this.count() }
};
</script>

<style scoped>
#todo-title-container {
	display: flex;
	justify-content: space-between;
}
ul {
	padding-left: 0px;
	margin-bottom: 0px;
}
li {
	list-style: none;
	padding: 8px 0px;
	padding-left: 4px;
	border-bottom: 1px solid #b2b2b2;
}
input[type=checkbox] {
	border-radius: 50%;
	appearance: none;
	width: 18px;
	height: 18px;
	border: 1px solid #b2b2b2;
	vertical-align: middle;
}
input[type=checkbox]:checked {
	background-color: #862583;
}
input[type=checkbox]:checked ~ label {
	background: url(../assets/check.svg) no-repeat;
	width: 10px;
	height: 10px;
	display: inline-block;
}
input#svgCheck ~ span {
	padding-left: 6px;
	padding-right: 6px;
}
form {
	display: flex;
	flex-direction: row-reverse;
	justify-content: flex-end;
	border-bottom: 1px solid #b2b2b2;
	padding: 6px 0px;
}
form > button {
	border: none;
    padding-left: 14px;
    padding-right: 8px;
    background: unset;
    font-size: 20px;
    color: #b2b2b2;
}
form > input {
	border: none;
	width: 100%;
}
input[type=checkbox]:hover, button[type=submit]:hover {
	cursor: pointer;
}
</style>