<script>
	import { slide } from "svelte/transition";
	import { elasticInOut } from "svelte/easing";
	import TodoItem from "./TodoItem.svelte";
	
	let input = '';
	let todos = [];
	
	function addTodo() {
		if( input ) {
			let newTodo = {
				text: input,
				id: Math.random().toString(36).substr(2,9)
			}
			todos = [...todos, newTodo];
		}
		input = '';
	}
	
	function removeTodo(e) {
		console.log('removeTodo');
		let id = e.detail.id;
		
		const index = todos.findIndex( todo => todo.id === id );
		todos.splice(index, 1);
		todos = todos;
	}
	
</script>


<svelte:head>
	<link rel="stylesheet" type="text/css" href="https://cdn.jsdelivr.net/npm/bulma@0.8.0/css/bulma.min.css">
	<script src="https://use.fontawesome.com/releases/v5.3.1/js/all.js"></script>
</svelte:head>


<main class="container is-fluid">
	<div class="columns is-centered is-vcentered is-mobile">
		<div class="column is-narrow" style="width: 400px;">
			
			
			<h1 class="has-text-centered title">
				Svelte Todo	
			</h1>
			
			
			<form class="field has-addons" style="justify-content: center" on:submit|preventDefault={addTodo}>
				<div class="control">
					<input bind:value="{input}" class="input" type="text" placeholder="Que faire aujourd'hui ?">
				</div>
				<div class="control">
					<button class="button is-primary">
						<span class="icon is-small"><i class="fas fa-plus"></i></span>
					</button>
				</div>
			</form>
			
			
			<ul class:list={todos.length > 0}>
				{#each todos as todo (todo.id)}
					<TodoItem {...todo} on:removeTodo={removeTodo} />
				
				{:else}
					<li class="has-text-centered" transition:slide="{{delay: 600, duration: 300, easing: elasticInOut}}">
						Rien à faire aujourd'hui !
					</li>
				
				{/each}
			</ul>
			
			
		</div>
	</div>
</main>
