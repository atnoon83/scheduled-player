<script>
  import * as Tabs from "$lib/components/ui/tabs/index.js";
  import Setting from "$lib/components/Setting.svelte";
</script>

<main class="w-full">
    <Tabs.Root value="play" class="w-full">
        <Tabs.List class="w-full flex justify-around">
            <Tabs.Trigger value="play">Play List</Tabs.Trigger>
            <Tabs.Trigger value="schedule">Schedule List</Tabs.Trigger>
            <Tabs.Trigger value="setting">Setting</Tabs.Trigger>
        </Tabs.List>
        <Tabs.Content value="play">
            Play list here.
        </Tabs.Content>
        <Tabs.Content value="schedule">
            Scheduled list here.
        </Tabs.Content>
        <Tabs.Content value="setting">
            <Setting />
        </Tabs.Content>
    </Tabs.Root>
</main>

