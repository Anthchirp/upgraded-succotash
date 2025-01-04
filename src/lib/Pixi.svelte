<script lang="ts">
    import { getContext } from "svelte"
    import { Application, Sprite, Assets, Rectangle } from "pixi.js"
    import { onMount, onDestroy } from "svelte"
    import Infobox from "./Infobox.svelte"
    import { writable } from "svelte/store"

    let boundContainer: HTMLDivElement | null = $state(null)

    // Tooltip store
    const tooltip = writable<{ x: number; y: number; content: string } | null>(
        null,
    )

    import type { Unsubscriber, Writable } from "svelte/store"
    const globalDarkMode: Writable<Boolean | null> = getContext("darkmode")
    let globalDarkModeUnsubscribe: Unsubscriber | null

    onMount(() => {
        if (!boundContainer) return
        const appContainer: HTMLDivElement = boundContainer

        // Create the Pixi application
        const app = new Application()

        // Optional: Add any Pixi.js setup here
        const setup = async () => {
            await app.init({ backgroundAlpha: 0, resizeTo: appContainer })
            ;(globalThis as any).__PIXI_APP__ = app // eslint-disable-line

            // Append the canvas to the container
            if (appContainer) appContainer.appendChild(app.canvas)

            try {
                const texture = await Assets.load(
                    "https://pixijs.com/assets/bunny.png",
                )
                const bunny = new Sprite(texture)
                app.stage.addChild(bunny)
                bunny.x = app.screen.width / 2
                bunny.y = app.screen.height / 2
                bunny.anchor.set(0.5)

                // Add a ticker callback to move the sprite back and forth
                let elapsed = 0.0
                app.ticker.add((ticker) => {
                    elapsed += ticker.deltaTime / 20
                    bunny.x =
                        ((Math.cos(elapsed / 50.0) + 1.1) *
                            app.screen.width *
                            0.9) /
                        2
                    bunny.y =
                        ((Math.sin(elapsed / 50.0) + 1.1) *
                            app.screen.height *
                            0.9) /
                        2
                })

                bunny.eventMode = "static"
                bunny.on("pointerdown", (event) => {
                    event.stopPropagation()
                    const containerRect = appContainer?.getBoundingClientRect()
                    if (!containerRect) return
                    const { x, y } = event.global
                    tooltip.set({
                        x: x + containerRect.left + window.scrollX,
                        y: y + containerRect.top + window.scrollY,
                        content: `Sprite clicked! ${elapsed}`,
                    })
                })
            } catch (error) {
                console.error("Error loading assets:", error)
            }
            app.stage.interactive = true
            app.stage.hitArea = new Rectangle(
                0,
                0,
                app.screen.width,
                app.screen.height,
            )
            app.stage.on("pointerdown", () => {
                tooltip.set(null)
            })

            // Subscribe to global events
            globalDarkModeUnsubscribe =
                globalDarkMode.subscribe(updateColorTheme)
        }
        setup()

        function updateColorTheme(darkmode: Boolean | null) {
            if (darkmode == null || !app.renderer) {
                return
            }
            console.log("Pixi listener dark mode toggled", darkmode)
            app.renderer.background.color = darkmode ? 0x000000 : 0xffffff
        }

        // Cleanup when component is destroyed
        onDestroy(() => {
            app.destroy(true, { children: true })
            globalDarkModeUnsubscribe?.()
        })
    })
</script>

<div bind:this={boundContainer} class="h-screen w-screen"></div>

{#if $tooltip}
    <Infobox x={$tooltip.x} y={$tooltip.y} content={$tooltip.content} />
{/if}
