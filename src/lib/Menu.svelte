<script lang="ts">
  import { onMount, onDestroy } from "svelte";
  let menuButton: HTMLButtonElement | null = null;
  let menuSection: HTMLElement | null = null;

  const toggleMenu = () => {
    menuSection?.classList.toggle("hidden");
    menuSection?.classList.toggle("flex");
  };
</script>

<button
  bind:this={menuButton}
  onclick={toggleMenu}
  class="cursor-pointer text-8xl text-sky-600"
>
  &#9776;
</button>
<section
  bind:this={menuSection}
  onclick={toggleMenu}
  class="origin-top animate-open-menu hidden absolute top-0 bg-black w-full flex-col justify-content-center border border-green-400"
>
  <button class="self-end px-6 text-8xl text-sky-600">&times;</button>
  <nav class="flex flex-col items-center py-8" aria-label="mobile">
    <a
      href="#home"
      class="w-full text-center py-6 hover:opacity-90 border border-green-300"
      >Home</a
    >
  </nav>
</section>
