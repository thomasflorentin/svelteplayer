<script>
  import AudioPlayer from './AudioPlayer.svelte';
  import Track from './Track.svelte';

	let currentSrc = "";
	let currentCover = "";
  let audio;
	
  let audioTracks = [
		{
			id: Math.random()
						.toString(36)
						.substr(2, 9),
			src: 'https://sveltejs.github.io/assets/music/strauss.mp3',
			title: 'Strauss',
			cover: 'https://static.qobuz.com/images/artists/covers/medium/15bed9b001fab597a96242deaa8e5e2f.jpg'
		},
		{
			id: Math.random()
						.toString(36)
						.substr(2, 9),
			src: 'https://sveltejs.github.io/assets/music/holst.mp3',
			title: 'Holst',
			cover: 'http://caminodemusica.com/clasica/wp-content/uploads/2013/11/gustav-holst.jpg'
		},	
		{
			id: Math.random()
						.toString(36)
						.substr(2, 9),
			src: 'https://sveltejs.github.io/assets/music/satie.mp3',
			title: 'Satie',
			cover: 'https://i.cbc.ca/1.5053067.1552408489!/fileImage/httpImage/erik-satie.jpg'
		},
  ];
	
	const listenThisTitle = function(e) {
		
		player = document.getElementById('player');

		let id = e.detail.id; 
		let track = audioTracks.find(track => track.id === id);
			
		let this_src = track.src;
		let this_cover = track.cover;

		if( currentSrc === this_src) {
			alert('déjà en lecture');
			return;
		}
		else {
			currentSrc = this_src;
			currentCover = this_cover;
			
			player.load(); //call this to just preload the audio without playing
  		player.play(); //call this to play the song right away
		}
	}
</script>

<main>
	<div id="app" >
		<AudioPlayer currentSrc={currentSrc} currentCover={currentCover} />
		<ul class="tracks_list">
			{#each audioTracks as track}
				<Track {...track} on:listenThisTitle={listenThisTitle} />
			{/each}
		</ul>
	</div>
</main> 
<style>
	
	main {
		background: gray;
		display: flex;
		justify-content: center;
		align-items: center;
		height: 100vh;
	}
	#app {
		background: white;
		border: 1px solid gray;
		width: 400px;
		border-radius: 10px;
	}
	.tracks_list {
		list-style: none;
		padding: 0;
		margin: 0;
	}
</style>