<script>
		import { slide } from "svelte/transition";
		import { elasticInOut } from "svelte/easing";
	
		import { createEventDispatcher } from 'svelte';
		const dispatch = createEventDispatcher();
	
		export let text;
		export let id;
	
		function removeTodo() {
			dispatch('removeTodo', {
				id: id,
				text: text
			})
		}
	
</script>


	<li class="list-item" transition:slide="{{duration: 300, easing: elasticInOut}}">
		<div class="is-flex" style="align-items: center">
			<span class="is-pulled-left">{text}</span>
			<div style="flex:1"></div>
			<button class="button is-text is-pulled-right is-small" on:click={removeTodo}> 
				<span class="icon">
					<i class="fas fa-check"></i>
				</span>
			</button>
		</div>
	</li>


<style>
</style>