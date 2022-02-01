<script>
    import {page} from '$app/stores'  
    import {onMount} from 'svelte'

    let songResults = []
    onMount(async () => {
        let songId = $page.params.songId
     const iTunesSearched = await fetch(`https://itunes.apple.com/search?term=${songId}&entity=song`)
     const res = await iTunesSearched.json()
     songResults = res.results[0]

    })
</script>
 
 <section>
    <div class="mt-12 flex flex-col items-center justify-center">
        <h1 class="text-3xl font-bold text-center mb-12">{songResults.trackName}</h1>
        <img src={songResults.artworkUrl100} alt="img" class="w-1/4 rounded-md mb-12">
        <audio id='myAudio' controls src={songResults.previewUrl} />
    </div>
 </section>