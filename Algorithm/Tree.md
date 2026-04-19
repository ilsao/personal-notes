# Heap (Priority Queue)

heap 是完全二叉樹：除最後一層，其餘層全滿。最後一層應從左到右填。

heap 通常不會用指針存，而直接用數組。
- 左子節點：`2i+1` 
- 右子節點：`2i+2` 
- 父節點：`(i-1) / 2` 

max heap：root 值最大。

min heap：root 值最小。

建堆：從最後一個非葉節點做 heapify **down** (注意不是 heapify up)。即，從 $\left\lfloor  \frac{n}{2}  \right\rfloor+1$ 開始做。

heapify up：用在插入新元素時。
1. 新元素插入在末尾
2. 與 parent 作比較，若不滿足 heap 性質則 `swap(parent, child)` 
	1. swap 後遞歸向上確認 (child 被換到上面，繼續與上層 parent 比較)
3. 否則，滿足 heap 性質停止遞歸

```cpp
void heapify_up(vector<int>& heap, int i) {
    if (i == 0) return;  // 到 root 了
    int parent = (i - 1) / 2;
    if (heap[parent] >= heap[i]) return;
    swap(heap[parent], heap[i]);
    heapify_up(heap, parent);
}
```

heapify down：用在刪除舊元素時。
1. 彈出堆頂
2. 取末尾元素放置在堆頂
3. 與 (最大 (max heap) 或最小 (min heap)) child 比較，若不滿足性質則 `swap(parent, child)` 
	1. swap 後遞歸向下確認 (parent(當前處理節點) 與自己的 child 交換，繼續與下層 child 比較)
4. 否則，滿足 heap 性質停止遞歸

```cpp
void heapify_down(vector<int>& heap, int i) {
    int n = heap.size();

    int left = 2 * i + 1;
    int right = 2 * i + 2;
    int largest = i;

    if (left < n && heap[left] > heap[largest])
        largest = left;

    if (right < n && heap[right] > heap[largest])
        largest = right;

    if (largest == i) return;

    swap(heap[i], heap[largest]);

    heapify_down(heap, largest);
}
```

若想對 `priority_queue` 自定義比較規則，使用：

``` cpp
struct cmp {
	bool operator()(ListNode* a, ListNode* b) {
		return a->val > b->val;         // min heap
	}
};
priority_queue<ListNode*, vector<ListNode*>, cmp> q;
```

# Binary Search Tree

## Search

```cpp
TreeNode* searchBST(TreeNode* root, int val) {
        if (!root)              return nullptr;
        if (root->val > val)    return searchBST(root->left, val);
        if (root->val < val)    return searchBST(root->right, val);
        return root;
}
```

# Insert

```cpp
TreeNode* insertIntoBST(TreeNode* root, int val) {
    if (!root) return new TreeNode(val);

    if (val < root->val)
        root->left = insertIntoBST(root->left, val);
    else if (val > root->val)
        root->right = insertIntoBST(root->right, val);

    return root;
}
```

## Delete

分三種情況：
- 刪除節點是葉子節點：直接刪除
- 刪除節點只有一個孩子：用孩子頂替
- 刪除節點有兩個孩子：用右子樹的最小節點 (最左) 的值頂替，然後刪除右子樹最小節點 (遞歸，最終會回到上兩種情況)。

```cpp
TreeNode* findMin(TreeNode* root) {
	if (!root)          return nullptr;
	if (!root->left)    return root;
	return              findMin(root->left);
}

TreeNode* deleteNode(TreeNode* root, int key) {
	if (!root)              return nullptr;
	if (root->val > key)    root->left = deleteNode(root->left, key);
	if (root->val < key)    root->right = deleteNode(root->right, key);
	if (root->val == key) {
		if (!root->left && !root->right) {
			delete root;
			// note: if we didn't return nullptr, 
			// we returned a pointer that points to an unallocated area
			return nullptr;
		}
		else if (!root->left && root->right) {
			TreeNode* tmp = root;
			root = root->right;
			delete tmp;
		}
		else if (root->left && !root->right) {
			TreeNode* tmp = root;
			root = root->left;
			delete tmp;
		}
		else {
			TreeNode* tmp = findMin(root->right);
			root->val = tmp->val;
			// same issue as above, 
			// if we delete root->right, we should set root->right = nullptr
			root->right = deleteNode(root->right, tmp->val);
		}
	}
	return root;
}
```

# AVL Tree

平衡因子：左子樹高度 - 右子樹高度

AVL 樹需滿足：
- BST
- 平衡因子 $\leq 1$ 

## Rotate

![[Pasted image 20260329143532.png|842]]

## Insert

插入後，檢查失衡情況。若失衡：
- 離**插入節點最近的失衡節點**的失衡因子為：
	- $-2$：右子樹高
		- 檢查右子樹失衡因子：
			- $-1$：RR
			- $+1$：RL
	- $+2$：左子樹高
		- 檢查左子樹失衡因子：
			- $-1$：LR
			- $+1$：LL

注意到我們只需調整離插入節點最近的失衡節點即可。

### LL, RR, LR, RL

LL:

![[Pasted image 20260329144809.png|670]]

RR:

![[Pasted image 20260329144830.png|686]]

LR:

![[Pasted image 20260329144904.png|700]]

RL:

![[Pasted image 20260329144924.png|693]]

## Delete

先按照 BST 規則刪除。

然後，依次對祖先檢查平衡因子，若失衡則調整。然後，遞歸檢查祖先節點的失衡狀況與調整。

# Red Black Tree

## Definition

紅黑樹需滿足：
- BST
- 根節點與葉節點 (包含 null) 都是黑色
- 從上到下不存在兩個連續紅色節點
- 每個節點到任意葉節點的所有路徑上，黑色節點數相同

紅黑樹最長路徑不超過最短路徑兩倍，否則不可能路徑黑節點數相同。

## Insert

插入節點默認為紅色。

若插入節點為根節點，變黑。

若父節點為黑，不用調整。

否則：
- 若插入節點的叔叔為紅 (祖先的子樹們太紅，顏色下推)：
	- 叔父爺反色 (父黑、叔黑、祖父紅)
	- 將爺爺變為待處理節點，向上調整
	- 將根節點調整為黑
- 若插入節點的叔叔為黑：
	- LL：對祖先右旋，對旋轉中心點與旋轉點變色 (父與祖先)
	- RR：對祖先左旋，對旋轉中心點與旋轉點變色
	- LR：對父左旋，再對祖先右旋，對旋轉中心點與旋轉點變色 (插入節點與祖先)
	- RL：對父右旋，再對祖先左旋，對旋轉中心點與旋轉點變色
	- 變色又可記成：新樹根與祖先交換顏色

```
插入紅節點

若為根 → 染黑
若父黑 → 結束

若父紅：
    若叔紅：
        父叔黑，祖父紅
        往上處理祖父
    若叔黑：
        LL / RR：單旋 + 父祖變色
        LR / RL：雙旋 + 新根與祖父變色

最後根為黑
```

[【红黑树 - 定义, 插入, 构建】 【精准空降到 10:52】 ](https://www.bilibili.com/video/BV1Xm421x7Lg/?share_source=copy_web&vd_source=a5527211b0718aa47c915126086231ec&t=652)

## Delete

![[Pasted image 20260329155339.png]]

[【红黑树 - 删除】 【精准空降到 20:40】]( https://www.bilibili.com/video/BV16m421u7Tb/?share_source=copy_web&vd_source=a5527211b0718aa47c915126086231ec&t=1240)