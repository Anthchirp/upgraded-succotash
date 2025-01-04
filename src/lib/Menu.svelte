<script lang="ts">
    let menuButton: HTMLButtonElement | null = null
    let menuSection: HTMLElement | null = null

    const toggleMenu = () => {
        menuSection?.classList.toggle("hidden")
        menuSection?.classList.toggle("flex")
        if (!menuButton) {
            return
        }
        menuButton.classList.toggle("toggle-btn")
        menuButton.ariaExpanded = (
            menuButton.ariaExpanded !== "true"
        ).toString()
    }
    function toggleMenuOnEscape(event: KeyboardEvent) {
        if (event.key === "Escape") {
            toggleMenu()
        }
    }
</script>

<button
    bind:this={menuButton}
    onclick={toggleMenu}
    class="relative h-8 w-8 cursor-pointer"
    aria-label="Toggle Menu"
    aria-haspopup="menu"
    aria-expanded="false"
    aria-controls="menuSection"
>
    <div
        class="absolute top-4 -mt-0.5 h-1 w-8 rounded bg-black transition-all duration-500 before:absolute before:h-1 before:w-8 before:-translate-x-4 before:-translate-y-3 before:rounded before:bg-black before:transition-all before:duration-500 before:content-[''] after:absolute after:h-1 after:w-8 after:-translate-x-4 after:translate-y-3 after:rounded after:bg-black after:transition-all after:duration-500 after:content-[''] dark:bg-white dark:before:bg-white dark:after:bg-white"
    ></div>
</button>
<section
    bind:this={menuSection}
    onclick={toggleMenu}
    onkeydown={toggleMenuOnEscape}
    id="menuSection"
    class="top-68 justify-content-center absolute hidden w-full origin-top animate-open-menu flex-col border border-green-400 bg-white dark:bg-black"
    role="menu"
    tabindex="-1"
>
    <nav class="flex flex-col items-center py-8" aria-label="mobile">
        <a
            href="#home"
            class="w-full border border-green-300 py-6 text-center hover:opacity-90"
            >Home</a
        >
    </nav>
</section>
