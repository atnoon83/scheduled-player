<script>
  import * as ToggleGroup from "$lib/components/ui/toggle-group/index.js";
  import SunIcon from "@lucide/svelte/icons/sun";
  import MoonIcon from "@lucide/svelte/icons/moon";
  import SunMoonIcon from "@lucide/svelte/icons/sun-moon";

  import { resetMode, setMode } from "mode-watcher";


</script>

<ToggleGroup.Root type="single">
    <ToggleGroup.Item value="light" aria-label="Toggle Light Mode" onclick={() => setMode("light")}>
        <SunIcon class="size-4" />
    </ToggleGroup.Item>
    <ToggleGroup.Item value="dark" aria-label="Toggle Dark Mode" onclick={() => setMode("dark")}>
        <MoonIcon class="size-4" />
    </ToggleGroup.Item>
    <ToggleGroup.Item value="system" aria-label="Toggle System Mode" onclick={() => resetMode()}>
        <SunMoonIcon class="size-4" />
    </ToggleGroup.Item>
</ToggleGroup.Root>