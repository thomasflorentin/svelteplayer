<script>
	import { createEventDispatcher } from 'svelte';
	const dispatch = createEventDispatcher();

	export let title;
	export let src;
	export let cover;
	export let id;
	
	const listenThisTitle = function(id) {
		dispatch('listenThisTitle', {
			id: id
		});
	}
</script>

<li id={id}> 
	<span>{title} </span>
	<button on:click|preventDefault={() => listenThisTitle(id) }>Ecouter ce titre</button>
</li>


<style>
	li {
		border-bottom: 1px solid;
		padding: 10px 20px;
		display: flex;
		justify-content: space-between;
		align-items: center;
	}
	li:last-child {
		border: none;
	}
	span {
		font-weight: bold;
		font-size: 20px;
		letter-spacing: .2em;
	}
	button {
		margin: 0;
		background: none;
		border-radius: 10px;
		font-size: 14px;
		padding: .5em 1em;
		border: 1px solid black;
	}
	button:hover {
		background: black;
		color: white;
		cursor: pointer;
	}
</style>