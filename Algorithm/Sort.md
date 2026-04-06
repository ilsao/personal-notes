# 自定義 Sort

```cpp
sort(list.begin(), list.end(), [](auto &a, auto &b) {
    return a.second > b.second;        // descending
});
```

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
	// heapify assumed that the subtrees have been heapified already
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
            // the subtrees have been heapified;
            // we need only check the swapped subtree
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
        // since we're building a max heap, 
        // swapping the first and the last item can move the largest number to the end
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
class Solution {
public:
    void merge(vector<int>& nums, int l, int mid, int r) {
        int left = l, right = mid + 1;
        int sz = r - l + 1;
        vector<int> tmp;
        tmp.reserve(sz);

        while (left <= mid && right <= r) {
            if (nums[left] <= nums[right])
                tmp.push_back(nums[left++]);
            else
                tmp.push_back(nums[right++]);
        }
        while (left <= mid)
            tmp.push_back(nums[left++]);
        while (right <= r)
            tmp.push_back(nums[right++]);

        for (int i = 0; i < sz; i++)
            nums[l + i] = tmp[i];
    }

    void mergeSort(vector<int>& nums, int l, int r) {
        if (l >= r) return;
        int mid = (l + r) / 2;
        mergeSort(nums, l, mid);
        mergeSort(nums, mid + 1, r);
        merge(nums, l, mid, r);
    }

    vector<int> sortArray(vector<int>& nums) {
        mergeSort(nums, 0, nums.size() - 1);
        return nums;
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

