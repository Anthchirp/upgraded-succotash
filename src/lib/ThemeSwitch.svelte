<script lang="ts">
    export const browser = !import.meta.env.SSR
    let darkMode = true
    if (browser) {
        darkMode =
            localStorage.theme === "dark" ||
            (!("theme" in localStorage) &&
                window.matchMedia("(prefers-color-scheme: dark)").matches)
        localStorage.setItem("theme", darkMode ? "dark" : "light")
    }

    let darkModeEnabled = $state(darkMode)
    let buttonLabel = $state("")

    function updatePageDarkMode() {
        if (darkModeEnabled) {
            document.documentElement.classList.add("dark")
            buttonLabel = "Disable dark mode"
            // $host().dispatchEvent(new CustomEvent(type))
        } else {
            document.documentElement.classList.remove("dark")
            buttonLabel = "Enable dark mode"
        }
    }

    function handleSwitchDarkMode(event: Event) {
        event.stopPropagation()
        darkModeEnabled = !darkModeEnabled
        localStorage.setItem("theme", darkModeEnabled ? "dark" : "light")
        updatePageDarkMode()
    }

    updatePageDarkMode()
</script>

<button
    onclick={handleSwitchDarkMode}
    class="group relative inline-flex items-center rounded-full bg-cyan-500 px-2 py-1.5 text-cyan-200 transition-colors duration-300 hover:bg-cyan-400 hover:text-cyan-50 focus:outline-none focus-visible:ring-2 focus-visible:ring-cyan-600 focus-visible:ring-offset-2 focus-visible:ring-offset-white dark:bg-slate-700 dark:text-slate-400 hover:dark:bg-slate-600 dark:hover:text-slate-200 dark:focus-visible:ring-slate-500"
    role="switch"
    type="button"
    tabindex="0"
    aria-checked={darkModeEnabled}
    ><span class="sr-only">{buttonLabel}</span><svg
        width="24"
        height="24"
        fill="none"
        aria-hidden="true"
        class="scale-0 transform transition-transform duration-500 dark:scale-100 dark:duration-300"
        ><path
            d="M15 12a3 3 0 1 1-6 0 3 3 0 0 1 6 0Z"
            fill="currentColor"
            stroke="currentColor"
            stroke-width="2"
            stroke-linecap="round"
            stroke-linejoin="round"
        ></path><path
            d="M12 4v1M18 6l-1 1M20 12h-1M18 18l-1-1M12 19v1M7 17l-1 1M5 12H4M7 7 6 6"
            stroke="currentColor"
            stroke-width="2"
            stroke-linecap="round"
            stroke-linejoin="round"
        ></path></svg
    ><svg
        width="24"
        height="24"
        fill="none"
        aria-hidden="true"
        class="duration:300 ml-3.5 scale-100 transform transition-transform dark:scale-0 dark:duration-500"
        ><path
            d="M18 15.63c-.977.52-1.945.481-3.13.481A6.981 6.981 0 0 1 7.89 9.13c0-1.185-.04-2.153.481-3.13C6.166 7.174 5 9.347 5 12.018A6.981 6.981 0 0 0 11.982 19c2.67 0 4.844-1.166 6.018-3.37ZM16 5c0 2.08-.96 4-3 4 2.04 0 3 .92 3 3 0-2.08.96-3 3-3-2.04 0-3-1.92-3-4Z"
            fill="currentColor"
            stroke="currentColor"
            stroke-width="2"
            stroke-linecap="round"
            stroke-linejoin="round"
        ></path></svg
    ><span
        class="absolute left-0.5 top-0.5 flex h-8 w-8 transform items-center justify-center rounded-full bg-yellow-400 transition duration-500 dark:translate-x-[2.625rem] dark:bg-white"
        ><svg
            width="24"
            height="24"
            fill="none"
            aria-hidden="true"
            class="flex-none scale-100 transform text-black opacity-100 transition duration-500 dark:scale-0 dark:opacity-0"
            ><path
                d="M15 12a3 3 0 1 1-6 0 3 3 0 0 1 6 0Z"
                fill="currentColor"
                stroke="currentColor"
                stroke-width="2"
                stroke-linecap="round"
                stroke-linejoin="round"
            ></path><path
                d="M12 4v1M18 6l-1 1M20 12h-1M18 18l-1-1M12 19v1M7 17l-1 1M5 12H4M7 7 6 6"
                stroke="currentColor"
                stroke-width="2"
                stroke-linecap="round"
                stroke-linejoin="round"
            ></path></svg
        ><svg
            width="24"
            height="24"
            fill="none"
            aria-hidden="true"
            class="-ml-6 flex-none scale-0 transform text-slate-700 opacity-0 transition duration-500 dark:scale-100 dark:opacity-100"
            ><path
                d="M18 15.63c-.977.52-1.945.481-3.13.481A6.981 6.981 0 0 1 7.89 9.13c0-1.185-.04-2.153.481-3.13C6.166 7.174 5 9.347 5 12.018A6.981 6.981 0 0 0 11.982 19c2.67 0 4.844-1.166 6.018-3.37ZM16 5c0 2.08-.96 4-3 4 2.04 0 3 .92 3 3 0-2.08.96-3 3-3-2.04 0-3-1.92-3-4Z"
                fill="currentColor"
                stroke="currentColor"
                stroke-width="2"
                stroke-linecap="round"
                stroke-linejoin="round"
            ></path></svg
        ></span
    ></button
>
