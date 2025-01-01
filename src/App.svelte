<script lang="ts">
  import svelteLogo from "./assets/svelte.svg";
  import viteLogo from "/vite.svg";
  import Counter from "./lib/Counter.svelte";
  import ThemeSwitch from "./lib/ThemeSwitch.svelte";
  import Pixi from "./lib/Pixi.svelte";
</script>

<main>
  <div class="flex flex-row justify-center">
    <a href="https://vite.dev" target="_blank" rel="noreferrer">
      <img
        src={viteLogo}
        class="h-36 p-6 logo will-change-[filter] transition-[filter] duration-300 hover:drop-shadow-[0_0_2em_rgba(100,108,255,0.67)]"
        alt="Vite Logo"
      />
    </a>
    <a href="https://svelte.dev" target="_blank" rel="noreferrer">
      <img
        src={svelteLogo}
        class="h-36 p-6 logo svelte will-change-[filter] transition-[filter] duration-300 hover:drop-shadow-[0_0_2em_rgba(255,62,0,0.67)]"
        alt="Svelte Logo"
      />
    </a>
  </div>
  <h1 class="p-8 font-bold text-5xl leading-tight">Vite + Svelte</h1>

  <div class="p-8">
    <Counter />
  </div>

  <p class="my-4 leading-6">
    Check out <a
      class="text-sky-600 hover:text-sky-500 dark:hover:text-sky-700"
      href="https://github.com/sveltejs/kit#readme"
      target="_blank"
      rel="noreferrer">SvelteKit</a
    >, the official Svelte app framework powered by Vite!
  </p>

  <p class="text-neutral-500 my-4 leading-6">
    Click on the Vite and Svelte logos to learn more
  </p>

  <ThemeSwitch />
  <Pixi />
</main>
