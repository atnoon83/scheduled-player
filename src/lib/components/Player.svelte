<script>
  import {Button} from "$lib/components/ui/button/index.js";
  import {Slider} from "$lib/components/ui/slider/index.js";
  import {Label} from "$lib/components/ui/label/index.js";

  import PlayIcon from "@lucide/svelte/icons/play";
  import PauseIcon from "@lucide/svelte/icons/pause";
  import StepBackIcon from "@lucide/svelte/icons/step-back";
  import StepForwardIcon from "@lucide/svelte/icons/step-forward";

  let value = $state(23);
  let maxValue = $state(100);
  let isPlaying = $state(false);
</script>

<div class="flex flex-col items-center gap-4 p-4 w-full">
    <div class="text-center">
        <h3>Music Name</h3>
    </div>
    <div class="w-full grid grid-cols-[1fr_10fr_1fr] items-center gap-2">
        <div class="flex justify-center">
            <Label>
                {value}
            </Label>
        </div>
        <Slider type="single" max={100} step={1} bind:value/>
        <div class="flex justify-center">
            <Label>
                {maxValue}
            </Label>
        </div>
    </div>
    <div class="flex items-center gap-4">
        <Button variant="secondary" size="icon" class="rounded-full  size-12">
            <StepBackIcon />
        </Button>
        <Button variant="default" size="icon" class="rounded-full  size-12" onclick={() => isPlaying = !isPlaying}>
            {#if isPlaying}
                <PauseIcon />
            {:else}
                <PlayIcon />
            {/if}
        </Button>
        <Button variant="secondary" size="icon" class="rounded-full size-12">
            <StepForwardIcon />
        </Button>
    </div>
</div>