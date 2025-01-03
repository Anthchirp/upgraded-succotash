<script lang="ts">
    import { onMount, onDestroy } from "svelte"
    let menuButton: HTMLButtonElement | null = null
    let menuSection: HTMLElement | null = null

    const toggleMenu = () => {
        menuSection?.classList.toggle("hidden")
        menuSection?.classList.toggle("flex")
        menuButton?.classList.toggle("toggle-btn")
    }
</script>

<button
    bind:this={menuButton}
    onclick={toggleMenu}
    class="relative h-8 w-8 cursor-pointer text-8xl text-sky-600"
>
    <div
        class="absolute top-4 -mt-0.5 h-1 w-8 rounded bg-white transition-all duration-500 before:absolute before:h-1 before:w-8 before:-translate-x-4 before:-translate-y-3 before:rounded before:bg-white before:transition-all before:duration-500 before:content-[''] after:absolute after:h-1 after:w-8 after:-translate-x-4 after:translate-y-3 after:rounded after:bg-white after:transition-all after:duration-500 after:content-['']"
    ></div>
    <!-- &#9776; -->
</button>
<section
    bind:this={menuSection}
    onclick={toggleMenu}
    class="top-68 justify-content-center absolute hidden w-full origin-top animate-open-menu flex-col border border-green-400 bg-black"
>
    <!-- <button class="self-end px-6 text-8xl text-sky-600">&times;</button> -->
    <nav class="flex flex-col items-center py-8" aria-label="mobile">
        <a
            href="#home"
            class="w-full border border-green-300 py-6 text-center hover:opacity-90"
            >Home</a
        >
    </nav>
</section>
