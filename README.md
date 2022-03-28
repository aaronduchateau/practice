# practice

You are given an m x n binary matrix mat of 1's (representing soldiers) and 0's (representing civilians). The soldiers are positioned in front of the civilians. That is, all the 1's will appear to the left of all the 0's in each row.

A row i is weaker than a row j if one of the following is true:

The number of soldiers in row i is less than the number of soldiers in row j.
Both rows have the same number of soldiers and i < j.
Return the indices of the k weakest rows in the matrix ordered from weakest to strongest.

# Example

Input: mat = 
[[1,1,0,0,0],
 [1,1,1,1,0],
 [1,0,0,0,0],
 [1,1,0,0,0],
 [1,1,1,1,1]], 
k = 3
Output: [2,0,3]
Explanation: 
The number of soldiers in each row is: 
- Row 0: 2 
- Row 1: 4 
- Row 2: 1 
- Row 3: 2 
- Row 4: 5 
The rows ordered from weakest to strongest are [2,0,3,1,4].

# Solution
    /**
    * @param {number[][]} mat
    * @param {number} k
    * @return {number[]}
    */
    var kWeakestRows = function(mat, k) {
        let indexesAndCount = [];
        for (let i = 0; i < mat.length; i++){
            let row = mat[i];
            let count = row.reduce((prev, cur)=> prev + cur, 0);
            indexesAndCount.push([i,count]);
        }
        let indexesAndCountSorted = indexesAndCount.sort((a,b)=> a[1] - b[1]);
        return indexesAndCountSorted.map(x=>x[0]).slice(0,k);
    };
