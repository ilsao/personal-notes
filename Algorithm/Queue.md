# Queue

## 核心概念

Queue 適合描述「按到達順序處理」的問題，例如：

- 任務排隊
- 層序遍歷
- BFS
- 模擬排隊系統
- 維護某種時間先後順序

在 C++ 中，標準庫提供了 `queue`，底層通常基於 `deque` 實現。

## 基本操作

隊列最常見的操作有：
- `push(x)`：將元素加入隊尾
- `pop()`：彈出隊首元素
- `front()`：訪問隊首元素
- `back()`：訪問隊尾元素
- `empty()`：判斷是否為空
- `size()`：返回元素個數

Queue 不支持隨機訪問，因此它不適合：
- 需要快速訪問中間元素的場景
- 需要維護有序性的場景
- 需要頻繁在中間插入刪除的場景

## 適用場景

當題目具有以下特徵時，通常可以考慮 Queue：

- 按照先後順序處理元素
- 當前處理的元素，會產生新的待處理元素
- 一層一層地擴展狀態
- 模擬真實排隊流程
- 需要維護「最早進來但尚未處理」的元素

這類描述經常對應：

- BFS
- 樹的層序遍歷
- 圖的最短步數問題（無權圖）
- 數據流式處理
- 某些模擬題

## 典型模板

### 1. 普通隊列模板

```cpp
queue<int> q;

q.push(1);
q.push(2);
q.push(3);

while (!q.empty()) {
    int x = q.front();
    q.pop();
    // 處理 x
}
```

### 2. 二叉樹層序遍歷模板

```cpp
vector<vector<int>> levelOrder(TreeNode* root) {
    vector<vector<int>> ans;
    if (!root) return ans;

    queue<TreeNode*> q;
    q.push(root);

    while (!q.empty()) {
        int sz = q.size();
        vector<int> level;

        for (int i = 0; i < sz; i++) {
            TreeNode* node = q.front();
            q.pop();

            level.push_back(node->val);

            if (node->left) q.push(node->left);
            if (node->right) q.push(node->right);
        }

        ans.push_back(level);
    }

    return ans;
}
```

### 3. BFS 模板（圖）

```cpp
#include <vector>
#include <queue>
using namespace std;

vector<int> bfs(int n, vector<vector<int>>& graph, int start) {
    vector<int> order;
    vector<bool> visited(n, false);
    queue<int> q;

    q.push(start);
    visited[start] = true;

    while (!q.empty()) {
        int u = q.front();
        q.pop();
        order.push_back(u);

        for (int v : graph[u]) {
            if (!visited[v]) {
                visited[v] = true;
                q.push(v);
            }
        }
    }

    return order;
}
```

### 4. 求無權圖最短步數模板

```cpp
#include <vector>
#include <queue>
using namespace std;

int shortestPath(int n, vector<vector<int>>& graph, int start, int target) {
    vector<int> dist(n, -1);
    queue<int> q;

    q.push(start);
    dist[start] = 0;

    while (!q.empty()) {
        int u = q.front();
        q.pop();

        if (u == target) return dist[u];

        for (int v : graph[u]) {
            if (dist[v] == -1) {
                dist[v] = dist[u] + 1;
                q.push(v);
            }
        }
    }

    return -1;
}
```

## 易錯點

### 1. `pop()` 不返回值

C++ 的 `queue.pop()` 只是刪除隊首元素，不會返回它。  
正確寫法是：

```cpp
int x = q.front();
q.pop();
```

### 2. 訪問 `front()` 前要先判空

若隊列為空，直接訪問 `front()` 或 `back()` 會出錯。

### 3. BFS 中 visited 的標記時機

應當在入隊時就標記 `visited`，而不是出隊時。  
否則同一節點可能被重複加入多次。

錯誤風格：

```cpp
if (!visited[v]) q.push(v);
// 之後才 visited[v] = true;
```

正確風格：

```cpp
if (!visited[v]) {
    visited[v] = true;
    q.push(v);
}
```

### 4. 分層遍歷時要先記錄當前層大小

若你在遍歷當前層時直接用 `q.size()` 作為循環條件，隊列大小會隨著子節點入隊而變化，導致層次混亂。

正確做法：

```cpp
int sz = q.size();
for (int i = 0; i < sz; i++) {
    ...
}
```

