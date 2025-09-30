<script>
  import Player from "$lib/components/Player.svelte";
  import {ScrollArea} from "$lib/components/ui/scroll-area/index.js";
</script>

<div>
    <h1 class="text-2xl ">Playlist</h1>
    <ScrollArea class="h-[calc(100vh-210px)] w-full border rounded-lg">
        <ul class="space-y-2">
            {#each Array(20) as _, index}
                <li>
                    Track {index + 1}
                </li>
            {/each}
        </ul>
    </ScrollArea>

    <Player/>
</div>