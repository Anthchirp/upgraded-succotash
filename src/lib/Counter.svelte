<script lang="ts">
    let count: number = $state(0)
    const increment = (event: Event) => {
        event.stopPropagation()
        count += 1
    }
</script>

<button
    onclick={increment}
    class="rounded-lg border border-transparent bg-zinc-100 px-5 py-2.5 transition-colors duration-200 hover:border-sky-600 dark:bg-zinc-900"
>
    count is {count}
</button>
