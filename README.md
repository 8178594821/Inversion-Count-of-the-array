# Inversion-Count-of-the-array

📝 Problem
Count number of pairs (i, j) such that i < j and arr[i] > arr[j].

🚀 Approach
- Use merge sort
- Count inversions during merge

⏱ Complexity
Time: O(n log n)
Space: O(n)

code:
class Solution {

    static int count = 0;

    public int inversionCount(int[] arr) {
        count = 0;
        mergeSort(arr, 0, arr.length - 1);
        return count;
    }

    void mergeSort(int[] arr, int left, int right) {
        if (left >= right) return;

        int mid = (left + right) / 2;

        mergeSort(arr, left, mid);
        mergeSort(arr, mid + 1, right);
        merge(arr, left, mid, right);
    }

    void merge(int[] arr, int left, int mid, int right) {

        int[] temp = new int[right - left + 1];
        int i = left, j = mid + 1, k = 0;

        while (i <= mid && j <= right) {
            if (arr[i] <= arr[j]) {
                temp[k++] = arr[i++];
            } else {
                temp[k++] = arr[j++];
                count += (mid - i + 1);
            }
        }

        while (i <= mid) temp[k++] = arr[i++];
        while (j <= right) temp[k++] = arr[j++];

        for (int x = 0; x < temp.length; x++) {
            arr[left + x] = temp[x];
        }
    }
}

🧪 Dry Run
arr = [2,4,1,3,5]
Step:

Split →
[2,4] and [1,3,5]

Merge step:

Compare:

👉 2 > 1 → inversion
👉 4 > 1 → inversion
👉 4 > 3 → inversion

👉 Total = 3

I used merge sort to count inversions efficiently by counting how many elements in the left subarray are greater than elements in the right.

If you found this helpful, give it a ⭐ and follow for more such solutions 🚀
