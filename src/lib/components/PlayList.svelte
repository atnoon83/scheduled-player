<script>
  import Player from "$lib/components/Player.svelte";
  import {ScrollArea} from "$lib/components/ui/scroll-area/index.js";
  import * as Card from "$lib/components/ui/card/index.js";
  import {Button} from "$lib/components/ui/button/index.js";

  let {title = "Playlist"} = $props();
  let playList = $state([
    {id: 1, title: "Song One", file: "/path/to/song1.mp3", time: 345},
    {id: 2, title: "Song Two", file: "/path/to/song2.mp3", time: 290},
    {id: 3, title: "Song Three", file: "/path/to/song3.mp3", time: 310},
    {id: 4, title: "Song Four", file: "/path/to/song4.mp3", time: 275},
    {id: 5, title: "Song Five", file: "/path/to/song5.mp3", time: 330},
    {id: 6, title: "Song Six", file: "/path/to/song6.mp3", time: 260},
    {id: 7, title: "Song Seven", file: "/path/to/song7.mp3", time: 300},
    {id: 8, title: "Song Eight", file: "/path/to/song8.mp3", time: 280},
    {id: 9, title: "Song Nine", file: "/path/to/song9.mp3", time: 320},
    {id: 10, title: "Song Ten", file: "/path/to/song10.mp3", time: 295},
    // Add more items as needed
  ]);

  let editSong = (event, song) => {
    event.stopPropagation();
    console.log("edit button clicked for song: ", song);
  }
  let deleteSong = (event, song) => {
    event.stopPropagation();
    let number = playList.findIndex(item => item.id === song.id);
    if (number !== -1) {
      playList.splice(number, 1);
    }
  }

  let handleDrop = (state) => {
    console.log("handle drop", JSON.stringify(state));
    const {draggedItem, targetContainer} = state;
    const dragIndex = playList.findIndex((item) => item.id === draggedItem.id);
    const dropIndex = parseInt(targetContainer ?? '0');

    if (dragIndex !== -1 && !isNaN(dropIndex)) {
      const [item] = playList.splice(dragIndex, 1);
      playList.splice(dropIndex, 0, item);
    }
  }
</script>

<div class="flex flex-col justify-center items-center">
    <h1 class="text-2xl ">{title}</h1>
    <ScrollArea class="h-[calc(100vh-230px)] w-full border rounded-lg">
        {#each playList as song,index(song.id)}
            <Card.Root
                    onclick={(e) => {console.log(`card clicked for song: ${song.title}`)}}
                    class="m-4 cursor-pointer">
                <Card.Header>
                    <Card.Title>{song.title}</Card.Title>
                    <Card.Description>{song.file}</Card.Description>
                </Card.Header>
                <Card.Content>
                    <p>This is the content of song {song.title} @ {song.file}</p>
                </Card.Content>
                <Card.Footer class="flex items-center gap-4">
                    <Button size="sm" onclick={(e) => {editSong(e, song)}}>Edit</Button>
                    <Button size="sm" onclick={(e) => {deleteSong(e, song)}}>Delete</Button>
                </Card.Footer>
            </Card.Root>
        {/each}
    </ScrollArea>
    <Player/>
</div>