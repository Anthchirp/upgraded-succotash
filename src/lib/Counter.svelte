<script lang="ts">
  let count: number = $state(0);
  const increment = () => {
    count += 1;
  };
</script>

<button
  onclick={increment}
  class="border bg-zinc-100 dark:bg-zinc-900 hover:border-sky-600 border-transparent rounded-lg px-5 py-2.5 transition-colors duration-200"
>
  count is {count}
</button>
