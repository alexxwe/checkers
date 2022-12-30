<script lang="ts">
    /**
     * 0:empty cell
     * 1:Wdama
     * 2:Bdama
     */
    const map: number[][] = [
        [2, 0, 2, 0, 2, 0, 2, 0],
        [0, 2, 0, 2, 0, 2, 0, 2],
        [2, 0, 2, 0, 2, 0, 2, 0],
        [0, 0, 0, 0, 0, 0, 0, 0],
        [0, 0, 0, 0, 0, 0, 0, 0],
        [0, 1, 0, 1, 0, 1, 0, 1],
        [1, 0, 1, 0, 1, 0, 1, 0],
        [0, 1, 0, 1, 0, 1, 0, 1],
    ]
    /**
     * pinta la ficha en la celda en la que esta <3
     */
    function colorPiece(cell: number): string {
        const colors: Record<number, string> = {
            1: 'bg-white',
            2: 'bg-black',
        }
        return colors[cell] ?? ''
    }
</script>

<section class="container mx-auto grid border-4 border-black" style="width:704px">
    <!-- rows -->
    {#each map as row, rowIdx}
        <div class="grid grid-cols-8">
            <!-- cells per row -->
            {#each row as cell, cellIdx}
                <div class="bg-red-400 w-20 h-20 m-1 flex justify-center items-center">
                    <div class="{colorPiece(cell)} w-12 h-12 rounded-full" />
                    {rowIdx}
                    {cellIdx}
                </div>
            {/each}
        </div>
    {/each}
</section>
