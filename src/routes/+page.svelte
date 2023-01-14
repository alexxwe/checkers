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
        [0, 1, 0, 0, 0, 0, 0, 1],
        [0, 0, 0, 0, 2, 0, 2, 0],
        [0, 1, 0, 1, 0, 1, 0, 1],
        [1, 0, 0, 0, 1, 0, 1, 0],
        [0, 1, 0, 1, 0, 1, 0, 1],
    ]
    let isWhiteTurn = true
    let cellSelected: number[] | null = null



    function tintCell(cellSelected: number[] | null, y: number, x: number, cellValue: number): string {
        // cellSelected: 5 3
         
        const cellColor = (y + x) % 2 ? 'bg-orange-200' : 'bg-yellow-900'
        if (!cellSelected) return cellColor
        let yChange: number = 1

        if(isWhiteTurn == true){ yChange = 1}
        else{ yChange =-1}
        
        if ((cellSelected[0] === y + yChange) && (cellSelected[1] === x-1)) return 'bg-green-400'
        if ((cellSelected[0] === y + yChange) && (cellSelected[1] === x+1)) return 'bg-green-400'



        // if(isWhiteTurn === true){
        //     if ((cellSelected[0] === y-yChange) && (cellSelected[1] === x-1)) return 'bg-green-400'
        //     if ((cellSelected[0] === y-yChange) && (cellSelected[1] === x+1)) return 'bg-green-400'
        // }
        // else{
        //     if ((cellSelected[0] === y+yChange) && (cellSelected[1] === x-1)) return 'bg-green-400'
        //     if ((cellSelected[0] === y+yChange) && (cellSelected[1] === x+1)) return 'bg-green-400'
        // }





        // let yChange: number = 1
        // // checks if is the green cell (possible move cell)
        
        // if (cellValue === 2) yChange = -1
        
        // if ((cellSelected[0] === y+yChange) && (cellSelected[1] === x-1)) return 'bg-green-400'
        // if ((cellSelected[0] === y+yChange) && (cellSelected[1] === x+1)) return 'bg-green-400'
        


        // //invent
        // if (cellValue === 1) yChange = +1
        // if ((cellSelected[0] === y-yChange) && (cellSelected[1] === x-1)) return 'bg-purple-400'
        // if ((cellSelected[0] === y-yChange) && (cellSelected[1] === x+1)) return 'bg-purple-400'



        // checks if is the yellow cell (current cell)
        if (cellSelected[0] !== y) return cellColor
        if (cellSelected[1] !== x) return cellColor
        return 'bg-yellow-400'
    }




    function tintPiece(cell: number): string {
        const colors: Record<number, string> = {
            1: 'bg-white',
            2: 'bg-black',
        }
        return colors[cell] ?? ''
    }

    /**
     * Handle when you click a piece
     */
    function handleClick(y: number, x: number): void {
        cellSelected = [y,x]
        console.log(y, x)
    }
</script>

<h2 class="m-5 text-center text-2xl {isWhiteTurn ? 'text-white' : ''}">{isWhiteTurn ? "White's" : "Black's"} Turn</h2>
{cellSelected}
<section class="container mx-auto grid border-4 border-black" style="width:704px">
    <!-- rows -->
    {#each map as row, rowIdx}
        <div class="grid grid-cols-8">
            <!-- cells per row -->
            {#each row as cell, cellIdx}
                <div class="{tintCell(cellSelected, rowIdx, cellIdx, cell)} m-1 flex h-20 w-20 items-center justify-center">
                    {#if cell}
                    <button on:click={() => handleClick(rowIdx, cellIdx)} class="{tintPiece(cell)} h-12 w-12 rounded-full" />
                    {/if}
                    {rowIdx}
                    {cellIdx}
                </div>
            {/each}
        </div>
    {/each}
</section>
