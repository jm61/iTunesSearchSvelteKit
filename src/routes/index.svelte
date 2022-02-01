<script>
import {goto} from '$app/navigation'
let searched = ''
let active = true
$: !searched ? active = true : active = false
const search = () => {
    goto(`${searched}`)
}
</script>

<section>
    <div class="flex flex-col items-center justify-center">
        <div class="text-5xl text-center text-white font-semibold mb-12">Search for an Artist</div>
        <form class="w-full flex rounded-md bg-white bg-opacity-20 p-1 border border-white border-opacity-30" >
            <input type="search" bind:value={searched} placeholder="enter the name of an Artist" class="w-4/5 bg-transparent text-white">
            <button disabled={active} on:click={search} class="w-1/5 p-2 rounded-md bg-white font-medium">Search</button>
        </form>
        
    </div>
</section>