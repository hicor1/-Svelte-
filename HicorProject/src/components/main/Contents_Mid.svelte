<script>
    import Stat from "./Stat.svelte";
    import SearchBar from "./Search_bar.svelte";
    import MainTable from "./MainTable.svelte";
</script>

<div class="flex flex-col w-full border-opacity-50 mt-8 mb-8">

    <Stat />

    <div class="divider"></div>

    <div class="mockup-window border border-base-300">
        <div class="flex flex-col justify-center px-4 py-4 border-t border-base-300">
            <SearchBar />
            <MainTable />
        </div>
    </div>

    <div class="divider"></div>

    <div class="grid h-20 card bg-base-300 rounded-box place-items-center">content</div>

</div>
