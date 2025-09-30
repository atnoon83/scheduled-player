<script>
  import {Button} from "$lib/components/ui/button/index.js";
  import {Slider} from "$lib/components/ui/slider/index.js";
  import {Label} from "$lib/components/ui/label/index.js";

  let value = $state(23);
  let maxValue = $state(100);
</script>

<div class="flex flex-col items-center gap-4 p-4">
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
        <Button>Prev</Button>
        <Button>
            Play/Pause
        </Button>
        <Button>Next</Button>
    </div>
</div>