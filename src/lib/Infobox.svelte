<script lang="ts">
    interface Props {
        x: number;
        y: number;
        content: string;
    }

    let { x, y, content }: Props = $props();
</script>

<div class="tooltip" style="left: {x}px; top: {y}px;">
    {content}
</div>

<style>
    .tooltip {
        position: absolute;
        background: red;
        padding: 10px;
        border: 4px solid purple;
        border-radius: 5px;
        box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.2);
        z-index: 1000;
    }
</style>
