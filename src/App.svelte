<script lang="ts">
    import svelteLogo from "./assets/svelte.svg"
    import viteLogo from "/vite.svg"
    import Pixi from "./lib/Pixi.svelte"
    import Menu from "./lib/Menu.svelte"

    // Global variable to track dark mode activation
    import { writable } from "svelte/store"
    import { setContext } from "svelte"
    const darkMode = writable<Boolean | null>(null)
    setContext("darkmode", darkMode)

    darkMode.subscribe((thing) => {
        if (thing === null) {
            return
        }
    })
</script>

<main>
    <Pixi />
    <Menu />
</main>
