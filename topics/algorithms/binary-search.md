# Binary Search

> Divide and Conquer Algorithm <sup>2</sup>

- Assumes data is sorted<sup>5</sup>
- Big O is `O(log n)`
- Takes the midpoint or average of data and starts searching there
- Instead of going through each item one at a time, it eliminates values that are not close to intended search value<sup>6</sup>
- Can be done iteratively (`for`, `while`) or recursively.

## Steps

- Given `[0,1,2,3,4]` and looking for what index has `3` as a value with binary search
- First run, both value `0` (from first index position) and value `4` (last index position) are added together, then divided by `2` to get average.
- Average comes out to `2` as `(0 + 4) / 2 = 2`
- Go to array position `2` and get value: `2`
- Is `2` equal to `3`? No, continue on logic check
- Is `2` smaller than `3`? Yes, so move the left index check from first array index `0` to array index `3`, which was previous check value `+1`.
- Repeat steps:
- Get average of the value `3` from left check and `4` from right check.
- Average comes out to `3.5`
- Always round down average
- Look at value at array index `3`
- Is the value, `3` equal to search value, `3`? Yes! Return the index of `3` as that is our current search position in the array.
- While loop exists as `return` has been used.

The following is an implementation of Binary Search in JavaScript:<sup>1,4</sup>
```js
function binarySearch(arr, val){
  let left = 0;
  let right = arr.length - 1;
  let middle, current;
  while ( right >= left ) {
    middle = Math.floor((left + right) / 2)
    current = arr[middle];
    if (current === val) {
      return middle;
    } else if (current < val) {
      left = middle + 1;
    } else if (current > val) {
      right = middle - 1;
    }
  }
  return -1;
}
```

## Recursive Binary Search

```js
// one disadvantage is you have to input the low
// and high values in addition:
function binarySearchR(arr, low, high, val) {
  if ( low > high ) {
    return -1;
  }
  let mid = Math.floor((low + high) / 2);
  if ( val === arr[mid] ) {
    return mid;
  } else if ( val < arr[mid] ) {
    return binarySearchR(arr, low, mid - 1, val);
  } else {
    return binarySearchR(arr, mid + 1, high, val);
  }
}
// created a helper function to get the process started:
function binarySearchIt(arr, val) {
  return binarySearchR(arr, 0, arr.length, val);
}
binarySearchIt([0,4,5,8,10,12]);
```

-----

## Sources

- <sup id="source1">1</sup> [Intro to Binary Search](https://dev.to/racheladaw/intro-to-binary-search-385o)
- <sup id="source2">2</sup> [Binary Search Algorithm Explained](https://dev.to/techlearners/binary-search-algorithm-explained-2nn5)
- <sup id="source3">3</sup> [Linear, Binary, and Interpolation Search Algorithms Explained](https://dev.to/christinamcmahon/linear-binary-and-interpolation-search-algorithms-explained-55ni#binary-search)
- <sup id="source4">4</sup> [Writing a Binary Search Algorithm in JavaScript](https://dev.to/seanwelshbrown/writing-a-binary-search-algorithm-in-javascript-5fa6)
- <sup id="source5">5</sup> [Algorithms Every Programmer Should Know](https://dev.to/surajondev/algorithms-every-programmer-should-know-part-1-searching-algorithm-1hd3#binary-search)
- <sup id="source6">6</sup> [Searching Algorithms](https://dev.to/code_regina/searching-algorithms-24gd#intro-to-binary-search)
- <sup id="source7">7</sup> [Binary Search](https://github.com/trekhleb/javascript-algorithms/tree/master/src/algorithms/search/binary-search)
- <sup id="source8">8</sup> [Iterative and Recursive Binary Search Algorithm](https://iq.opengenus.org/binary-search-iterative-recursive/#recursivebinarysearch)
