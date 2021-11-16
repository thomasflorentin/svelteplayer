<script>
  export let currentSrc;
	export let currentCover;
</script>

<div class="player_container">
	<img src={currentCover} alt="cover">

	<audio
		id="player"
		controls>
		<source id="audioSource" src="{currentSrc}">
		<track kind="captions" />
	</audio>
</div>


<style>
	
	.player_container {
		width: 100%;
		height: 300px;
		background: rgba(20,50,200, .2);
		font-size: 1px;
		display: flex;
		align-items: flex-end;
		border-radius: 10px;
		position: relative;
	}
	#player {
		width: 100%;
		z-index: 2;
	}
	img {
		position: absolute;
		width: 100%;
		height: 100%;
		object-fit: cover;
		z-index: 1;
	}
</style>