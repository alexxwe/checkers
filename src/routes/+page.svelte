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
    let isWhiteTurn = true
    let cellSelected: number[] | null = null
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
    /**
     * Handle when you click a piece
     */
    function handleClick(x: number, y: number): void {}
</script>

<h2 class="m-5 text-center text-2xl {isWhiteTurn ? 'text-white' : ''}">{isWhiteTurn ? "White's" : "Black's"} Turn</h2>

<section class="container mx-auto grid border-4 border-black" style="width:704px">
    <!-- rows -->
    {#each map as row, rowIdx}
        <div class="grid grid-cols-8">
            <!-- cells per row -->
            {#each row as cell, cellIdx}
                <div class="{(rowIdx + cellIdx) % 2 ? 'bg-orange-200' : 'bg-yellow-900'} m-1 flex h-20 w-20 items-center justify-center">
                    {#if cell}
                    <button on:click={() => handleClick(cellIdx, rowIdx)} class="{colorPiece(cell)} h-12 w-12 rounded-full" />
                    {/if}
                    {rowIdx}
                    {cellIdx}
                </div>
            {/each}
        </div>
    {/each}
</section>
