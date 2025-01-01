<script lang="ts">
  import { Application, Sprite, Assets } from "pixi.js";
  import { onMount, onDestroy } from "svelte";

  let boundContainer: HTMLDivElement | null = null;
  let app: Application;

  onMount(() => {
    if (!boundContainer) return;
    const appContainer: HTMLDivElement = boundContainer;

    // Create the Pixi application
    const app = new Application();

    // Optional: Add any Pixi.js setup here
    const setup = async () => {
      await app.init({ background: "#1099bb", resizeTo: appContainer });
      //document.body.appendChild(app.canvas);
      // Append the canvas to the container
      if (appContainer) appContainer.appendChild(app.canvas);

      try {
        const texture = await Assets.load(
          "https://pixijs.com/assets/bunny.png",
        );
        const bunny = new Sprite(texture);
        app.stage.addChild(bunny);
        bunny.x = app.screen.width / 2;
        bunny.y = app.screen.height / 2;
        bunny.anchor.set(0.5);
      } catch (error) {
        console.error("Error loading assets:", error);
      }
    };
    setup();

    // Cleanup when component is destroyed
    onDestroy(() => {
      app.destroy(true, { children: true });
    });
  });
</script>

<div
  bind:this={boundContainer}
  style="width: 800px; height: 600px;"
  class="border-red-400 border-4"
></div>
