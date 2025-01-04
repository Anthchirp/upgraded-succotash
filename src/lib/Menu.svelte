<script lang="ts">
    import Counter from "./Counter.svelte"
    import ThemeSwitch from "./ThemeSwitch.svelte"

    let menuButton: HTMLButtonElement | null = $state(null)
    let menuSection: HTMLElement | null = $state(null)

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
    class="fixed right-16 top-16 z-10 h-8 w-8 cursor-pointer"
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
    class="justify-content-center fixed right-12 top-12 hidden w-64 origin-top-right animate-open-menu flex-col rounded-lg border-2 border-slate-300 bg-slate-50 transition-colors duration-500 dark:border-slate-700 dark:bg-slate-950"
    role="menu"
    tabindex="-1"
>
    <nav class="flex flex-col items-center pb-6 pt-3" aria-label="mobile">
        <div class="mb-3 w-full pl-3 text-left">
            <ThemeSwitch />
        </div>
        <a
            href="#home"
            class="w-full py-5 text-center text-xl hover:bg-slate-300 dark:hover:bg-slate-700"
            >Home</a
        >
        <div class="p-3">
            <Counter />
        </div>
    </nav>
</section>
