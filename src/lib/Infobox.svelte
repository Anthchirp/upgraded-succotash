<script lang="ts">
    interface Props {
        x: number
        y: number
        content: string
    }

    let { x, y, content }: Props = $props()
</script>

<div
    class="tooltip sha absolute z-50 rounded-md border-4 border-purple-700 bg-red-500 p-3 shadow-lg shadow-purple-300 transition-colors duration-500 dark:shadow-purple-700"
    style="left: {x}px; top: {y}px;"
>
    {content}
</div>
