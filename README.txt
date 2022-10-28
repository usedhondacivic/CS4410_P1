This implementation does suffer from starvation. 
If NPUSH_OPEN + NPUSH_CLOSE - NPOP < MAX_SIZE, then the validator thread may never run and starve.
If push and pop threads alternate, they can also continue freeing each others gate infinitely, starving a validate thread.
A different order could fix this, but this implementation does allow threads to starve.