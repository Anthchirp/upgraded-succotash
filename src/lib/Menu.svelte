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
    class="relative w-8 h-8 cursor-pointer text-8xl text-sky-600"
>
    <div
        class="bg-white w-8 h-1 rounded absolute top-4 -mt-0.5 before:content-[''] transition-all duration-500 before:bg-white before:h-1 before:rounded before:absolute before:w-8 before:transition-all before:duration-500 before:-translate-x-4 before:-translate-y-3 after:content-[''] after:bg-white after:h-1 after:rounded after:absolute after:w-8 after:transition-all after:duration-500 after:-translate-x-4 after:translate-y-3"
    ></div>
    <!-- &#9776; -->
</button>
<section
    bind:this={menuSection}
    onclick={toggleMenu}
    class="origin-top animate-open-menu hidden absolute top-68 bg-black w-full flex-col justify-content-center border border-green-400"
>
    <!-- <button class="self-end px-6 text-8xl text-sky-600">&times;</button> -->
    <nav class="flex flex-col items-center py-8" aria-label="mobile">
        <a
            href="#home"
            class="w-full text-center py-6 hover:opacity-90 border border-green-300"
            >Home</a
        >
    </nav>
</section>
