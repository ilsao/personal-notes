# Heap Sort

若想對 `priority_queue` 自定義比較規則，使用：

``` cpp
struct cmp {
	bool operator()(ListNode* a, ListNode* b) {
		return a->val > b->val;         // min heap
	}
};
priority_queue<ListNode*, vector<ListNode*>, cmp> q;
```

``` cpp
class Solution {
public:
    void heapify(vector<int>& nums, int i, int n) {
        int left  = 2 * i + 1;
        int right = 2 * i + 2;
        int largest = i;
        if (left < n)
            largest = nums[i] > nums[left] ? i : left;
        if (right < n)
            largest = nums[largest] > nums[right] ? largest : right;
        if (largest != i) {
            swap(nums[i], nums[largest]);
            heapify(nums, largest, n);
        }
    }

    vector<int> sortArray(vector<int>& nums) {
        int sz = nums.size();

        // 1. build heap - heapify starts from the last non-leaf node
        int last = sz / 2 - 1;
        for (int i = last; i >= 0; i--)
            heapify(nums, i, sz);

        // 2. sort - swap the first item and the last one (remember to heapify)
        // since we're building max heap, swap the first and the last one can move the largest number to the end
        int n = sz;
        for (int i = 0; i < sz; i++) {
            swap(nums[0], nums[sz - i - 1]);
            heapify(nums, 0, --n);
        }
        return nums;
    }
};
```

# Merge Sort

基本思路：不斷將數組拆分，直到最小單元，然後兩兩合併。

``` cpp
#include <vector>
using namespace std;

class Solution {
public:
    void merge(vector<int>& arr, int left, int mid, int right) {
        vector<int> temp;
        int i = left;
        int j = mid + 1;

        while (i <= mid && j <= right) {
            if (arr[i] <= arr[j]) {
                temp.push_back(arr[i++]);
            } else {
                temp.push_back(arr[j++]);
            }
        }

        while (i <= mid) temp.push_back(arr[i++]);
        while (j <= right) temp.push_back(arr[j++]);

        for (int k = 0; k < temp.size(); k++) {
            arr[left + k] = temp[k];
        }
    }

    void mergeSort(vector<int>& arr, int left, int right) {
        if (left >= right) return;

        int mid = left + (right - left) / 2;

        mergeSort(arr, left, mid);
        mergeSort(arr, mid + 1, right);

        merge(arr, left, mid, right);
    }
};
```

# Quick Sort

基本思路：選定某元素作為 pivot，將比 pivot 小的都放在 pivot 左側，比 pivot 大的都放右側。持續此行為直到結束。

```cpp
class Solution {
public:
    int partition(vector<int>& nums, int l, int r) {
        int pivot = nums[l];
        while (l < r) {
            while (r > l && nums[r] > pivot)
                r--;
            // check the condition after the update
            if (r > l)
                nums[l++] = nums[r];
            while (r > l && nums[l] < pivot)
                l++;
            // we have to check here also
            if (r > l)
                nums[r--] = nums[l];
        }
        nums[l] = pivot;
        return l;
    }

    void quicksort(vector<int>& nums, int l, int r) {
        if (l >= r)
            return;
        int p = partition(nums, l, r);
        quicksort(nums, l, p - 1);
        // notice that we have to start at p + 1 (p has been processed)
        quicksort(nums, p + 1, r);
    }

    vector<int> sortArray(vector<int>& nums) {
        quicksort(nums, 0, nums.size() - 1);
        return nums;
    }
};
```