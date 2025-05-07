# Chương 3: Lộ trình học thuật toán & cấu trúc dữ liệu

[English Version](en.md)

## Tổng quan về lộ trình học

Lộ trình học được chia thành các chủ đề và kỹ thuật quan trọng sau, giúp bạn xây dựng nền tảng vững chắc để chinh phục các bài toán lập trình và phỏng vấn kỹ thuật:

---

### 1. Cấu trúc dữ liệu cơ bản

#### Mảng (Array) & Chuỗi (String)

**Mảng (Array)**
- **Định nghĩa:** Mảng là cấu trúc dữ liệu lưu trữ các phần tử liên tiếp trong bộ nhớ, cho phép truy cập trực tiếp qua chỉ số.
- **Ưu điểm:** Truy cập phần tử bất kỳ O(1), đơn giản, hiệu quả bộ nhớ.
- **Nhược điểm:** Kích thước cố định, thêm/xóa ở giữa tốn O(n).
- **Khi nào nên dùng?**
  - Khi cần truy cập nhanh theo chỉ số.
  - Khi số lượng phần tử biết trước hoặc không thay đổi nhiều.
  - Khi cần thao tác với dãy số, chuỗi ký tự, hoặc dữ liệu liên tục.
- **Ví dụ:**
```python
arr = [1, 2, 3, 4, 5]
print(arr[2])  # 3
arr.append(6)  # Thêm cuối
arr.pop(1)     # Xóa phần tử ở chỉ số 1
```

**Chuỗi (String)**
- **Định nghĩa:** Chuỗi là một dãy ký tự, dùng để lưu trữ và xử lý văn bản.
- **Ưu điểm:** Hỗ trợ nhiều thao tác (cắt, nối, tìm kiếm, so sánh), dễ dùng.
- **Nhược điểm:** Không thể thay đổi trực tiếp (immutable), nối nhiều chuỗi lớn có thể kém hiệu quả.
- **Khi nào nên dùng?**
  - Khi cần lưu trữ, xử lý văn bản, dữ liệu dạng ký tự.
  - Khi cần thao tác với các bài toán kiểm tra chuỗi con, đảo chuỗi, so sánh, tìm kiếm mẫu.
- **Ví dụ:**
```python
s = "hello"
print(s[::-1])  # Đảo chuỗi: 'olleh'
print("ell" in s)  # True
```

**Con trỏ đôi (Two Pointers)**
- **Định nghĩa:** Dùng hai con trỏ để duyệt mảng/chuỗi, thường cho các bài toán tìm cặp, subarray, đảo ngược.
- **Ưu điểm:** Tối ưu thời gian, giảm độ phức tạp từ O(n^2) xuống O(n), dễ cài đặt.
- **Nhược điểm:** Chỉ áp dụng cho bài toán có tính chất phù hợp (mảng đã sắp xếp, chuỗi liên tục...)
- **Khi nào nên dùng?**
  - Khi cần tìm cặp số, dãy con liên tiếp, hoặc xử lý chuỗi/mảng có tính chất liên tục.
  - Khi muốn tối ưu hóa các bài toán duyệt lồng nhau.
- **Ví dụ:**
```python
# Đảo ngược mảng bằng two pointers
arr = [1,2,3,4,5]
l, r = 0, len(arr)-1
while l < r:
    arr[l], arr[r] = arr[r], arr[l]
    l += 1
    r -= 1
# arr = [5,4,3,2,1]
```

**Sliding Window**
- **Định nghĩa:** Kỹ thuật dùng một cửa sổ di động trên mảng/chuỗi để giải quyết các bài toán subarray, substring.
- **Ưu điểm:** Tối ưu cho các bài toán tìm tổng, độ dài, tần suất liên tiếp.
- **Nhược điểm:** Chỉ áp dụng cho bài toán có tính chất liên tục.
- **Khi nào nên dùng?**
  - Khi cần tìm dãy con liên tiếp có tổng/tính chất tối ưu (max/min/đủ điều kiện).
  - Khi xử lý chuỗi/mảng với các bài toán subarray, substring.
- **Ví dụ:**
```python
# Sliding window: Tổng lớn nhất của dãy con độ dài k
arr = [1,3,-1,-3,5,3,6,7]
k = 3
max_sum = sum(arr[:k])
cur_sum = max_sum
for i in range(k, len(arr)):
    cur_sum += arr[i] - arr[i-k]
    max_sum = max(max_sum, cur_sum)
# max_sum = 16
```

**Xử lý chuỗi**
- **Định nghĩa:** Bao gồm các thao tác đảo chuỗi, so sánh chuỗi con, kiểm tra palindrome, v.v.
- **Ưu điểm:** Dễ thao tác, nhiều hàm hỗ trợ sẵn trong Python.
- **Nhược điểm:** Một số thao tác phức tạp có thể tốn thời gian nếu không tối ưu.
- **Khi nào nên dùng?**
  - Khi cần kiểm tra chuỗi con, đảo chuỗi, kiểm tra đối xứng, xử lý văn bản.
  - Khi giải các bài toán về pattern matching, palindrome, substring.
- **Ví dụ:**
```python
# Kiểm tra palindrome
s = "abccba"
print(s == s[::-1])  # True
# So sánh chuỗi con
print("abc" in "abcdef")  # True
```

#### Stack, Queue, Deque
- **Stack (Ngăn xếp)**
  - **Định nghĩa:** Stack là cấu trúc dữ liệu LIFO (Last In First Out), chỉ cho phép thêm/xóa ở một đầu (đỉnh stack).
  - **Ưu điểm:** Dễ cài đặt, thao tác O(1), phù hợp cho các bài toán duyệt cây, kiểm tra dấu ngoặc, undo/redo.
  - **Nhược điểm:** Không truy cập ngẫu nhiên phần tử giữa, dễ tràn stack nếu đệ quy sâu.
  - **Khi nào nên dùng?**
    - Khi cần lưu trữ trạng thái tạm thời (ví dụ: duyệt cây, quay lui).
    - Khi giải các bài toán kiểm tra biểu thức hợp lệ, undo/redo, backtracking.
  - **Ví dụ:**
  ```python
  stack = []
  stack.append(1)
  stack.append(2)
  print(stack.pop())  # 2
  ```

- **Queue (Hàng đợi)**
  - **Định nghĩa:** Queue là cấu trúc dữ liệu FIFO (First In First Out), thêm ở cuối và lấy ở đầu.
  - **Ưu điểm:** Quản lý tiến trình, BFS, buffer dữ liệu, thao tác O(1) với deque.
  - **Nhược điểm:** Không truy cập ngẫu nhiên phần tử giữa.
  - **Khi nào nên dùng?**
    - Khi cần xử lý dữ liệu theo thứ tự đến trước ra trước (BFS, hệ thống hàng đợi, buffer).
    - Khi cần quản lý các tác vụ, tiến trình, hoặc dữ liệu luồng.
  - **Ví dụ:**
  ```python
  from collections import deque
  q = deque()
  q.append(1)
  q.append(2)
  print(q.popleft())  # 1
  ```

- **Deque:**
  - Sliding window maximum/minimum.

```python
# Monotonic Stack: Tìm phần tử lớn hơn gần nhất bên phải
nums = [2,1,2,4,3]
stack, res = [], [-1]*len(nums)
for i in range(len(nums)):
    while stack and nums[i] > nums[stack[-1]]:
        res[stack.pop()] = nums[i]
    stack.append(i)
# res = [4,2,4,-1,-1]
```

#### Hash Table (Bảng băm)
- **Định nghĩa:** Bảng băm lưu trữ cặp key-value, cho phép truy cập, thêm, xóa phần tử O(1) trung bình.
- **Ưu điểm:** Truy cập nhanh, kiểm tra tồn tại hiệu quả, lưu trữ dữ liệu ánh xạ.
- **Nhược điểm:** Có thể xảy ra xung đột băm (collision), không duy trì thứ tự.
- **Khi nào nên dùng?**
  - Khi cần lưu trữ dữ liệu ánh xạ (key-value), đếm tần suất, kiểm tra tồn tại nhanh.
  - Khi giải các bài toán về tần suất, kiểm tra phần tử trùng, lưu vị trí, hashmap 2 chiều.
- **Ví dụ:**
```python
d = {}
d['a'] = 1
d['b'] = 2
print(d.get('a'))  # 1
# Đếm tần suất xuất hiện
from collections import Counter
s = "leetcode"
cnt = Counter(s)
# cnt = {'l':1, 'e':3, 't':1, 'c':1, 'o':1, 'd':1}
```

#### Set (Tập hợp)
- **Định nghĩa:** Set là cấu trúc dữ liệu lưu trữ các phần tử không trùng lặp, không quan tâm thứ tự.
- **Ưu điểm:** Kiểm tra tồn tại, thêm/xóa phần tử O(1) trung bình, loại bỏ trùng lặp dễ dàng.
- **Nhược điểm:** Không truy cập theo chỉ số, không lưu thứ tự phần tử.
- **Khi nào nên dùng?**
  - Khi cần kiểm tra sự tồn tại nhanh.
  - Khi cần loại bỏ phần tử trùng lặp trong danh sách.
- **Ví dụ:**
```python
s = set()
s.add(1)
s.add(2)
s.add(1)  # Không thêm trùng
print(2 in s)  # True
lst = [1,2,2,3]
unique = set(lst)  # {1,2,3}
```

#### Map (Ánh xạ/Dictionary nâng cao)
- **Định nghĩa:** Map (trong Python là dict) lưu trữ ánh xạ key-value, có thể lồng nhiều tầng (hashmap 2 chiều).
- **Ưu điểm:** Truy cập, thêm, xóa key-value O(1) trung bình, linh hoạt với kiểu key.
- **Nhược điểm:** Có thể tốn bộ nhớ nếu key phức tạp, không duy trì thứ tự trước Python 3.7.
- **Khi nào nên dùng?**
  - Khi cần lưu trữ dữ liệu dạng bảng, ánh xạ nhiều chiều (ví dụ: ma trận, đếm tần suất theo cặp).
  - Khi cần truy xuất nhanh theo nhiều khóa.
- **Ví dụ:**
```python
# Hashmap 2 chiều
from collections import defaultdict
d = defaultdict(dict)
d['a']['x'] = 1
d['a']['y'] = 2
d['b']['x'] = 3
print(d['a']['y'])  # 2
```

#### Deque (Double-ended Queue)
- **Định nghĩa:** Deque là hàng đợi hai đầu, cho phép thêm/xóa ở cả hai đầu với O(1).
- **Ưu điểm:** Hữu ích cho sliding window, queue hai đầu, thao tác đầu/cuối đều nhanh.
- **Nhược điểm:** Không truy cập ngẫu nhiên phần tử giữa.
- **Khi nào nên dùng?**
  - Khi cần thao tác cả hai đầu (bài toán sliding window, queue hai đầu, undo/redo nâng cao).
  - Khi cần tối ưu hóa các thuật toán như sliding window maximum/minimum.
- **Ví dụ:**
```python
from collections import deque
dq = deque([1,2,3])
dq.appendleft(0)  # Thêm vào đầu
dq.append(4)      # Thêm vào cuối
print(dq.pop())   # 4
print(dq.popleft()) # 0
```

---

### 2. Đệ quy & Quay lui (Recursion & Backtracking)
- **Subsets, Permutations, Combination Sum:**
  - Sinh tập con, hoán vị, tổ hợp tổng.
- **Sudoku Solver, N-Queens:**
  - Bài toán điền số, xếp quân hậu.

#### Đệ quy (Recursion)
- **Định nghĩa:** Đệ quy là kỹ thuật hàm tự gọi lại chính nó để giải quyết bài toán bằng cách chia nhỏ thành các bài toán con.
- **Ưu điểm:** Code ngắn gọn, tự nhiên cho các bài toán phân rã (cây, dãy số, tổ hợp).
- **Nhược điểm:** Dễ gây tràn stack nếu không có điều kiện dừng, hiệu suất kém nếu không tối ưu (lặp lại tính toán).
- **Khi nào nên dùng?**
  - Khi bài toán có thể chia nhỏ thành các bài toán con giống nhau (cây, dãy số, tổ hợp, tìm đường).
  - Khi cần duyệt cấu trúc dữ liệu phân cấp (cây, đồ thị).
- **Ví dụ:**
```python
# Tính giai thừa bằng đệ quy
def factorial(n):
    if n == 0:
        return 1
    return n * factorial(n-1)
print(factorial(5))  # 120
```

#### Quay lui (Backtracking)
- **Định nghĩa:** Quay lui là kỹ thuật thử tất cả các khả năng, quay lại trạng thái trước đó nếu không thỏa mãn điều kiện, thường dùng để sinh tổ hợp, hoán vị, giải sudoku, n-queens.
- **Ưu điểm:** Giải quyết được các bài toán tổ hợp, tìm tất cả đáp án, sinh cấu hình.
- **Nhược điểm:** Độ phức tạp cao (thường là O(2^n) hoặc hơn), dễ bị timeout nếu không cắt nhánh hợp lý.
- **Khi nào nên dùng?**
  - Khi cần liệt kê tất cả cấu hình hợp lệ (subsets, permutations, combination sum, sudoku, n-queens).
  - Khi không có công thức tổng quát, cần thử từng trường hợp.
- **Ví dụ:**
```python
# Sinh tất cả tập con bằng backtracking
res = []
def backtrack(start, path):
    res.append(path[:])
    for i in range(start, len(nums)):
        path.append(nums[i])
        backtrack(i+1, path)
        path.pop()
nums = [1,2,3]
backtrack(0,[])
print(res)
```

---

### 3. Tìm kiếm & Sắp xếp
- **Binary Search:**
  - Tìm kiếm trên mảng đã sắp xếp, tìm đáp án tối ưu (binary search on answer).
- **Merge Sort, Quick Sort:**
  - Sắp xếp chia để trị.
- **Heap (Priority Queue):**
  - Bài toán top-k, median, Dijkstra.

#### Binary Search (Tìm kiếm nhị phân)
- **Định nghĩa:** Tìm kiếm nhị phân là thuật toán tìm kiếm trên mảng đã sắp xếp bằng cách chia đôi phạm vi tìm kiếm sau mỗi bước.
- **Ưu điểm:** Tìm kiếm rất nhanh (O(log n)), dễ cài đặt, hiệu quả với dữ liệu lớn đã sắp xếp.
- **Nhược điểm:** Chỉ áp dụng cho mảng đã sắp xếp, không phù hợp với dữ liệu động thay đổi liên tục.
- **Khi nào nên dùng?**
  - Khi cần tìm kiếm nhanh trên mảng/list đã sắp xếp.
  - Khi giải các bài toán tìm đáp án tối ưu (binary search on answer).
- **Ví dụ:**
```python
arr = [1,3,5,7,9]
target = 5
l, r = 0, len(arr)-1
while l <= r:
    m = (l+r)//2
    if arr[m] == target:
        print(m)
        break
    elif arr[m] < target:
        l = m+1
    else:
        r = m-1
```

#### Merge Sort (Sắp xếp trộn)
- **Định nghĩa:** Merge Sort là thuật toán sắp xếp chia để trị, chia mảng thành các phần nhỏ rồi trộn lại theo thứ tự.
- **Ưu điểm:** Độ phức tạp O(n log n) ổn định, không bị ảnh hưởng bởi dữ liệu đầu vào, thích hợp cho dữ liệu lớn.
- **Nhược điểm:** Tốn bộ nhớ O(n) cho mảng tạm, cài đặt phức tạp hơn Bubble Sort.
- **Khi nào nên dùng?**
  - Khi cần sắp xếp ổn định, dữ liệu lớn, không quan tâm đến bộ nhớ phụ.
  - Khi cần sắp xếp các cấu trúc dữ liệu phức tạp.
- **Ví dụ:**
```python
def merge_sort(arr):
    if len(arr) <= 1:
        return arr
    mid = len(arr)//2
    left = merge_sort(arr[:mid])
    right = merge_sort(arr[mid:])
    res = []
    i = j = 0
    while i < len(left) and j < len(right):
        if left[i] < right[j]:
            res.append(left[i])
            i += 1
        else:
            res.append(right[j])
            j += 1
    res.extend(left[i:])
    res.extend(right[j:])
    return res
arr = [5,2,4,6,1,3]
print(merge_sort(arr))
```

#### Quick Sort (Sắp xếp nhanh)
- **Định nghĩa:** Quick Sort là thuật toán sắp xếp chia để trị, chọn một phần tử làm pivot và phân chia mảng thành hai phần nhỏ hơn/lớn hơn pivot.
- **Ưu điểm:** Trung bình rất nhanh (O(n log n)), không cần nhiều bộ nhớ phụ, cài đặt đơn giản.
- **Nhược điểm:** Trường hợp xấu nhất O(n^2) nếu chọn pivot không tốt, không ổn định.
- **Khi nào nên dùng?**
  - Khi cần sắp xếp nhanh, không yêu cầu ổn định, bộ nhớ hạn chế.
  - Khi dữ liệu không quá đặc biệt (không bị sắp xếp sẵn hoặc ngược).
- **Ví dụ:**
```python
def quick_sort(arr):
    if len(arr) <= 1:
        return arr
    pivot = arr[len(arr)//2]
    left = [x for x in arr if x < pivot]
    middle = [x for x in arr if x == pivot]
    right = [x for x in arr if x > pivot]
    return quick_sort(left) + middle + quick_sort(right)
arr = [3,6,8,10,1,2,1]
print(quick_sort(arr))
```

#### Heap (Priority Queue)
- **Định nghĩa:** Heap là cấu trúc dữ liệu cây nhị phân đặc biệt, luôn giữ phần tử lớn nhất (max-heap) hoặc nhỏ nhất (min-heap) ở gốc. Priority Queue là hàng đợi ưu tiên dựa trên heap.
- **Ưu điểm:** Lấy phần tử lớn/nhỏ nhất O(1), thêm/xóa O(log n), dùng cho bài toán top-k, median, Dijkstra.
- **Nhược điểm:** Không truy cập ngẫu nhiên phần tử giữa, không duy trì thứ tự toàn bộ.
- **Khi nào nên dùng?**
  - Khi cần lấy/lưu trữ phần tử lớn/nhỏ nhất liên tục (top-k, median, heap sort, Dijkstra).
  - Khi cần quản lý hàng đợi ưu tiên.
- **Ví dụ:**
```python
import heapq
arr = [3,1,4,1,5,9]
heapq.heapify(arr)
print(heapq.heappop(arr))  # 1 (min-heap)
heapq.heappush(arr, 2)
print(heapq.nsmallest(3, arr))  # 3 phần tử nhỏ nhất
```

---

### 4. Đồ thị (Graphs)
- **BFS, DFS:**
  - Duyệt đồ thị, tìm đường đi, kiểm tra liên thông.
- **Topological Sort:**
  - Sắp xếp thứ tự công việc (Kahn, DFS-based).
- **Shortest Path:**
  - Dijkstra, Bellman-Ford, Floyd-Warshall.
- **Union-Find (DSU):**
  - Kết nối thành phần, Minimum Spanning Tree (Kruskal, Prim).

**BFS (Breadth-First Search - Duyệt theo chiều rộng)**
- **Định nghĩa:** BFS là thuật toán duyệt đồ thị/lưới theo từng lớp, thăm các đỉnh gần nguồn nhất trước.
- **Ưu điểm:** Tìm đường đi ngắn nhất trên đồ thị không trọng số, dễ cài đặt với queue.
- **Nhược điểm:** Tốn bộ nhớ nếu đồ thị lớn, không phù hợp cho đồ thị có trọng số.
- **Khi nào nên dùng?**
  - Khi cần tìm đường đi ngắn nhất trên đồ thị/lưới không trọng số.
  - Khi cần duyệt theo từng lớp (level order traversal).
- **Ví dụ:**
```python
from collections import deque
graph = {0:[1,2], 1:[0,3], 2:[0], 3:[1]}
visited = set()
q = deque([0])
while q:
    node = q.popleft()
    if node in visited: continue
    visited.add(node)
    for nei in graph[node]:
        if nei not in visited:
            q.append(nei)
```

**DFS (Depth-First Search - Duyệt theo chiều sâu)**
- **Định nghĩa:** DFS là thuật toán duyệt đồ thị/lưới theo chiều sâu, đi càng xa càng tốt trước khi quay lại.
- **Ưu điểm:** Dễ cài đặt bằng đệ quy hoặc stack, dùng cho kiểm tra chu trình, thành phần liên thông.
- **Nhược điểm:** Có thể gây tràn stack với đồ thị lớn, không đảm bảo đường đi ngắn nhất.
- **Khi nào nên dùng?**
  - Khi cần duyệt toàn bộ đồ thị, kiểm tra chu trình, thành phần liên thông.
  - Khi giải các bài toán backtracking trên đồ thị/lưới.
- **Ví dụ:**
```python
graph = {0:[1,2], 1:[0,3], 2:[0], 3:[1]}
visited = set()
def dfs(u):
    if u in visited: return
    visited.add(u)
    for v in graph[u]:
        dfs(v)
dfs(0)
```

**Topological Sort (Sắp xếp thứ tự topo)**
- **Định nghĩa:** Sắp xếp topo là sắp xếp các đỉnh của đồ thị có hướng không chu trình (DAG) sao cho mọi cạnh u→v thì u đứng trước v.
- **Ưu điểm:** Xác định thứ tự thực hiện công việc, kiểm tra chu trình trong DAG.
- **Nhược điểm:** Chỉ áp dụng cho DAG, không áp dụng cho đồ thị có chu trình.
- **Khi nào nên dùng?**
  - Khi cần xác định thứ tự thực hiện các task có phụ thuộc.
  - Khi kiểm tra đồ thị có chu trình hay không.
- **Ví dụ (Kahn's algorithm):**
```python
from collections import deque, defaultdict
graph = {0:[1,2], 1:[3], 2:[3], 3:[]}
indegree = defaultdict(int)
for u in graph:
    for v in graph[u]:
        indegree[v] += 1
q = deque([u for u in graph if indegree[u]==0])
order = []
while q:
    u = q.popleft()
    order.append(u)
    for v in graph[u]:
        indegree[v] -= 1
        if indegree[v] == 0:
            q.append(v)
print(order)
```

**Dijkstra (Đường đi ngắn nhất trên đồ thị có trọng số dương)**
- **Định nghĩa:** Dijkstra là thuật toán tìm đường đi ngắn nhất từ một đỉnh đến các đỉnh khác trên đồ thị có trọng số dương.
- **Ưu điểm:** Hiệu quả với đồ thị thưa, trọng số dương, dùng heap để tối ưu.
- **Nhược điểm:** Không áp dụng cho trọng số âm, cài đặt phức tạp hơn BFS.
- **Khi nào nên dùng?**
  - Khi cần tìm đường đi ngắn nhất trên đồ thị có trọng số dương.
  - Khi giải các bài toán về mạng, đường đi tối ưu.
- **Ví dụ:**
```python
import heapq
graph = {0:[(1,2),(2,4)], 1:[(3,1)], 2:[(3,1)], 3:[]}
dist = {u:float('inf') for u in graph}
dist[0] = 0
pq = [(0,0)]
while pq:
    d,u = heapq.heappop(pq)
    if d > dist[u]: continue
    for v,w in graph[u]:
        if dist[v] > d+w:
            dist[v] = d+w
            heapq.heappush(pq, (dist[v], v))
print(dist)
```

**Union-Find (Disjoint Set Union - DSU)**
- **Định nghĩa:** DSU là cấu trúc dữ liệu quản lý các tập hợp rời rạc, hỗ trợ hợp nhất và kiểm tra cùng tập hợp.
- **Ưu điểm:** Hợp nhất, kiểm tra thành phần liên thông O(α(n)), dùng cho bài toán kết nối thành phần, Kruskal.
- **Nhược điểm:** Không truy xuất được tất cả phần tử trong tập hợp, chỉ kiểm tra đại diện.
- **Khi nào nên dùng?**
  - Khi cần quản lý các nhóm/tập hợp động (kết nối thành phần, kiểm tra chu trình, MST).
  - Khi giải các bài toán về mạng, đồ thị không hướng.
- **Ví dụ:**
```python
class DSU:
    def __init__(self, n):
        self.parent = list(range(n))
    def find(self, x):
        if self.parent[x] != x:
            self.parent[x] = self.find(self.parent[x])
        return self.parent[x]
    def union(self, x, y):
        self.parent[self.find(x)] = self.find(y)
dsu = DSU(5)
dsu.union(0,1)
dsu.union(3,4)
print(dsu.find(0) == dsu.find(1))  # True
```

**Minimum Spanning Tree (Kruskal, Prim)**
- **Định nghĩa:** MST là cây con của đồ thị nối tất cả các đỉnh với tổng trọng số nhỏ nhất. Kruskal dùng DSU, Prim dùng heap.
- **Ưu điểm:** Tìm mạng kết nối tối ưu, ứng dụng trong thiết kế mạng, điện, giao thông.
- **Nhược điểm:** Chỉ áp dụng cho đồ thị liên thông, cài đặt phức tạp với đồ thị lớn.
- **Khi nào nên dùng?**
  - Khi cần kết nối tối ưu các điểm (thiết kế mạng, đường đi).
  - Khi giải các bài toán về tối ưu hóa kết nối.
- **Ví dụ (Kruskal):**
```python
edges = [(1,0,1),(2,1,2),(3,0,2)]  # (weight, u, v)
parent = [i for i in range(3)]
def find(x):
    if parent[x]!=x:
        parent[x]=find(parent[x])
    return parent[x]
res = 0
for w,u,v in sorted(edges):
    if find(u)!=find(v):
        res += w
        parent[find(u)] = find(v)
print(res)
```

---

### 5. Quy hoạch động (Dynamic Programming - DP)
- **1D DP (Quy hoạch động một chiều)**
  - Fibonacci, Climbing Stairs, House Robber.
- **2D DP (Quy hoạch động hai chiều)**
  - Knapsack, Edit Distance, LCS.
- **DP nâng cao:**
  - Bitmask, tối ưu trạng thái, sliding window, prefix sum, memoization.

**1D DP (Quy hoạch động một chiều)**
- **Định nghĩa:** DP một chiều là kỹ thuật lưu trữ kết quả các bài toán con trong một mảng một chiều để tránh tính toán lặp lại.
- **Ưu điểm:** Tối ưu thời gian cho các bài toán có tính chất lặp lại, dễ cài đặt với các bài toán dãy số.
- **Nhược điểm:** Tốn bộ nhớ O(n), đôi khi khó xác định trạng thái phù hợp.
- **Khi nào nên dùng?**
  - Khi bài toán có thể chia nhỏ thành các bài toán con độc lập, kết quả bài toán lớn phụ thuộc bài toán nhỏ hơn.
  - Khi giải các bài toán dãy số, tối ưu hóa, đếm cách.
- **Ví dụ:**
```python
# Bậc thang (Climbing Stairs)
n = 5
dp = [0]*(n+1)
dp[0] = dp[1] = 1
for i in range(2, n+1):
    dp[i] = dp[i-1] + dp[i-2]
print(dp[n])  # Số cách leo lên n bậc thang
```

**2D DP (Quy hoạch động hai chiều)**
- **Định nghĩa:** DP hai chiều lưu trữ kết quả các bài toán con trong ma trận 2 chiều, thường dùng cho bài toán xâu, lưới, ba lô.
- **Ưu điểm:** Giải quyết được các bài toán phức tạp hơn như chuỗi con chung dài nhất, edit distance, knapsack.
- **Nhược điểm:** Tốn bộ nhớ O(n*m), cài đặt phức tạp hơn 1D DP.
- **Khi nào nên dùng?**
  - Khi trạng thái bài toán phụ thuộc vào hai biến (vị trí, trọng lượng, độ dài hai chuỗi).
  - Khi giải các bài toán chuỗi, lưới, ba lô.
- **Ví dụ:**
```python
# LCS (Longest Common Subsequence)
s1, s2 = "abcde", "ace"
dp = [[0]*(len(s2)+1) for _ in range(len(s1)+1)]
for i in range(1, len(s1)+1):
    for j in range(1, len(s2)+1):
        if s1[i-1] == s2[j-1]:
            dp[i][j] = dp[i-1][j-1]+1
        else:
            dp[i][j] = max(dp[i-1][j], dp[i][j-1])
print(dp[-1][-1])  # 3
```

**DP nâng cao (Bitmask, State Optimization)**
- **Định nghĩa:** Kỹ thuật tối ưu trạng thái DP bằng bitmask, sliding window, prefix sum, memoization để giảm bộ nhớ/thời gian.
- **Ưu điểm:** Giải quyết được các bài toán tổ hợp lớn, tối ưu hóa hiệu suất cho DP nhiều chiều.
- **Nhược điểm:** Cần tư duy trạng thái tốt, cài đặt phức tạp hơn.
- **Khi nào nên dùng?**
  - Khi số trạng thái lớn nhưng có thể mã hóa bằng bitmask hoặc tối ưu hóa bằng prefix sum, sliding window.
  - Khi giải các bài toán tổ hợp, tối ưu hóa, DP trên tập hợp.
- **Ví dụ:**
```python
# DP + Bitmask: Traveling Salesman Problem (TSP) cơ bản
n = 4
cost = [[0,1,15,6],[2,0,7,3],[9,6,0,12],[10,4,8,0]]
INF = float('inf')
dp = [[INF]*n for _ in range(1<<n)]
dp[1][0] = 0
for mask in range(1<<n):
    for u in range(n):
        if not (mask & (1<<u)): continue
        for v in range(n):
            if mask & (1<<v): continue
            dp[mask|(1<<v)][v] = min(dp[mask|(1<<v)][v], dp[mask][u]+cost[u][v])
print(min(dp[(1<<n)-1][i] for i in range(n)))
```

---

### 6. Cây (Trees)
- **Duyệt cây (Pre/In/Post-order Traversal)**
- **Binary Search Tree (BST)**
- **Lowest Common Ancestor (LCA)**
- **Segment Tree / Fenwick Tree (BIT):**

**Duyệt cây (Pre/In/Post-order Traversal)**
- **Định nghĩa:** Duyệt cây là quá trình thăm tất cả các node của cây nhị phân theo thứ tự nhất định: trước (pre), giữa (in), sau (post) node gốc.
- **Ưu điểm:** Dễ cài đặt bằng đệ quy hoặc stack, dùng cho nhiều bài toán phân tích cấu trúc cây.
- **Nhược điểm:** Có thể gây tràn stack với cây rất sâu nếu dùng đệ quy.
- **Khi nào nên dùng?**
  - Khi cần xử lý, in ra, hoặc phân tích cấu trúc cây nhị phân.
  - Khi giải các bài toán tổng hợp, tìm kiếm, kiểm tra tính chất cây.
- **Ví dụ:**
```python
# Duyệt in-order
res = []
def inorder(root):
    if not root: return
    inorder(root.left)
    res.append(root.val)
    inorder(root.right)
```

**Binary Search Tree (BST)**
- **Định nghĩa:** BST là cây nhị phân mà với mỗi node, tất cả node bên trái nhỏ hơn, bên phải lớn hơn node đó.
- **Ưu điểm:** Tìm kiếm, thêm, xóa O(log n) nếu cân bằng, dễ cài đặt.
- **Nhược điểm:** Nếu mất cân bằng, độ phức tạp có thể lên O(n).
- **Khi nào nên dùng?**
  - Khi cần lưu trữ dữ liệu có thứ tự, tìm kiếm, thêm, xóa nhanh.
  - Khi giải các bài toán về dãy số động, range query đơn giản.
- **Ví dụ:**
```python
class Node:
    def __init__(self, val):
        self.val = val
        self.left = self.right = None
# Thêm node vào BST
def insert(root, val):
    if not root: return Node(val)
    if val < root.val:
        root.left = insert(root.left, val)
    else:
        root.right = insert(root.right, val)
    return root
```

**Lowest Common Ancestor (LCA)**
- **Định nghĩa:** LCA là node tổ tiên chung thấp nhất của hai node trong cây.
- **Ưu điểm:** Tìm tổ tiên chung nhanh, ứng dụng trong phân tích cây, hệ thống phân cấp.
- **Nhược điểm:** Cần cài đặt thêm nếu cây không có parent pointer.
- **Khi nào nên dùng?**
  - Khi cần tìm mối quan hệ chung giữa hai node trong cây.
  - Khi giải các bài toán về phân cấp, truy vấn tổ tiên.
- **Ví dụ:**
```python
def lca(root, p, q):
    if not root or root==p or root==q: return root
    left = lca(root.left, p, q)
    right = lca(root.right, p, q)
    if left and right: return root
    return left or right
```

**Segment Tree (Cây đoạn)**
- **Định nghĩa:** Segment Tree là cấu trúc cây nhị phân dùng để truy vấn và cập nhật đoạn (range query) hiệu quả trên mảng.
- **Ưu điểm:** Truy vấn và cập nhật đoạn O(log n), hỗ trợ nhiều loại truy vấn (tổng, min, max).
- **Nhược điểm:** Cài đặt phức tạp, tốn bộ nhớ O(n).
- **Khi nào nên dùng?**
  - Khi cần truy vấn, cập nhật đoạn trên mảng động.
  - Khi giải các bài toán range query, dynamic programming nâng cao.
- **Ví dụ:**
```python
class SegmentTree:
    def __init__(self, arr):
        self.n = len(arr)
        self.tree = [0]*(2*self.n)
        for i in range(self.n):
            self.tree[self.n+i] = arr[i]
        for i in range(self.n-1,0,-1):
            self.tree[i] = self.tree[2*i] + self.tree[2*i+1]
    def query(self, l, r):
        res = 0
        l += self.n; r += self.n
        while l < r:
            if l%2:
                res += self.tree[l]
                l += 1
            if r%2:
                r -= 1
                res += self.tree[r]
            l //= 2; r //= 2
        return res
arr = [1,3,5,7,9,11]
st = SegmentTree(arr)
print(st.query(1,4))  # Tổng từ arr[1] đến arr[3]
```

**Fenwick Tree (Binary Indexed Tree - BIT)**
- **Định nghĩa:** Fenwick Tree là cấu trúc cây nhị phân dùng để truy vấn và cập nhật tổng đoạn hiệu quả, tối ưu bộ nhớ hơn Segment Tree.
- **Ưu điểm:** Truy vấn và cập nhật tổng đoạn O(log n), cài đặt đơn giản hơn Segment Tree, tốn ít bộ nhớ.
- **Nhược điểm:** Chỉ hỗ trợ một số loại truy vấn (tổng, min/max không linh hoạt như Segment Tree).
- **Khi nào nên dùng?**
  - Khi cần truy vấn/cập nhật tổng đoạn trên mảng động, ưu tiên bộ nhớ.
  - Khi giải các bài toán tổng prefix, inversion count.
- **Ví dụ:**
```python
class FenwickTree:
    def __init__(self, n):
        self.n = n
        self.tree = [0]*(n+1)
    def update(self, i, delta):
        while i <= self.n:
            self.tree[i] += delta
            i += i & -i
    def query(self, i):
        res = 0
        while i > 0:
            res += self.tree[i]
            i -= i & -i
        return res
ft = FenwickTree(6)
for idx, val in enumerate([1,3,5,7,9,11],1):
    ft.update(idx, val)
print(ft.query(3))  # Tổng từ 1 đến 3
```

---

### 7. Kỹ thuật khác
- **Greedy (Tham lam)**
  - Interval Scheduling, Jump Game, Huffman Encoding.
- **Sliding Window**
  - Các bài toán subarray.
- **Prefix Sum / Difference Array**
  - Tính tổng đoạn, cập nhật nhanh.
- **Bit Manipulation (Xử lý bit)**
  - XOR, kiểm tra bit thứ k.
- **Math:**
  - GCD, số nguyên tố, tổ hợp.
- **Trie (Cây tiền tố)**
  - Word Dictionary, Autocomplete.
- **Two Pointers (Hai con trỏ)**
  - Tìm cặp, 3Sum, remove duplicates.

**Greedy (Tham lam)**
- **Định nghĩa:** Greedy là kỹ thuật chọn phương án tối ưu cục bộ tại mỗi bước với hy vọng đạt được kết quả tối ưu toàn cục.
- **Ưu điểm:** Cài đặt đơn giản, chạy nhanh, không cần lưu trạng thái.
- **Nhược điểm:** Không phải lúc nào cũng cho kết quả tối ưu, cần chứng minh tính đúng đắn.
- **Khi nào nên dùng?**
  - Khi bài toán có tính chất tối ưu hóa và có thể chứng minh greedy là đúng (ví dụ: bài toán chọn hoạt động, Huffman, Jump Game).
- **Ví dụ:**
```python
# Interval Scheduling
intervals = [(1,3),(2,4),(3,5)]
intervals.sort(key=lambda x: x[1])
res, end = 0, -float('inf')
for s,e in intervals:
    if s >= end:
        res += 1
        end = e
print(res)
```

**Sliding Window**
- **Định nghĩa:** Kỹ thuật dùng một cửa sổ di động trên mảng/chuỗi để giải quyết các bài toán subarray, substring liên tiếp.
- **Ưu điểm:** Tối ưu cho các bài toán tìm tổng, độ dài, tần suất liên tiếp, giảm độ phức tạp từ O(n^2) xuống O(n).
- **Nhược điểm:** Chỉ áp dụng cho bài toán có tính chất liên tục.
- **Khi nào nên dùng?**
  - Khi cần tìm dãy con liên tiếp có tổng/tính chất tối ưu (max/min/đủ điều kiện).
- **Ví dụ:**
```python
# Sliding window: Tổng lớn nhất của dãy con độ dài k
arr = [1,3,-1,-3,5,3,6,7]
k = 3
max_sum = sum(arr[:k])
cur_sum = max_sum
for i in range(k, len(arr)):
    cur_sum += arr[i] - arr[i-k]
    max_sum = max(max_sum, cur_sum)
print(max_sum)
```

**Prefix Sum / Difference Array**
- **Định nghĩa:** Prefix Sum là mảng tích lũy tổng, Difference Array là mảng hiệu để cập nhật đoạn nhanh.
- **Ưu điểm:** Tính tổng đoạn, cập nhật đoạn nhanh O(1), giảm độ phức tạp cho nhiều bài toán.
- **Nhược điểm:** Chỉ áp dụng cho các phép toán cộng/trừ, không phù hợp với phép toán phức tạp.
- **Khi nào nên dùng?**
  - Khi cần tính tổng đoạn, cập nhật đoạn nhiều lần trên mảng.
- **Ví dụ:**
```python
# Prefix sum
arr = [1,2,3,4,5]
prefix = [0]*(len(arr)+1)
for i in range(len(arr)):
    prefix[i+1] = prefix[i] + arr[i]
print(prefix[3]-prefix[1])  # Tổng từ arr[1] đến arr[2]
```

**Bit Manipulation (Xử lý bit)**
- **Định nghĩa:** Kỹ thuật thao tác trực tiếp trên bit nhị phân của số nguyên để giải quyết bài toán tối ưu về tốc độ/bộ nhớ.
- **Ưu điểm:** Rất nhanh, tiết kiệm bộ nhớ, giải quyết các bài toán đặc biệt (mask, XOR, kiểm tra bit).
- **Nhược điểm:** Code khó đọc, dễ sai nếu không cẩn thận.
- **Khi nào nên dùng?**
  - Khi cần kiểm tra, thiết lập, đảo bit, hoặc giải các bài toán tổ hợp, trạng thái.
- **Ví dụ:**
```python
# Kiểm tra bit thứ k
n, k = 10, 2
print((n >> k) & 1)  # 1 nếu bit thứ k là 1
# XOR hai số
print(5 ^ 3)  # 6
```

**Trie (Cây tiền tố)**
- **Định nghĩa:** Trie là cây dùng để lưu trữ tập hợp các chuỗi, hỗ trợ tìm kiếm tiền tố nhanh.
- **Ưu điểm:** Tìm kiếm, thêm, kiểm tra tiền tố O(L) với L là độ dài chuỗi, hữu ích cho từ điển, autocomplete.
- **Nhược điểm:** Tốn bộ nhớ nếu lưu nhiều chuỗi dài, cài đặt phức tạp hơn set/map.
- **Khi nào nên dùng?**
  - Khi cần kiểm tra, lưu trữ, tìm kiếm tiền tố, từ điển, autocomplete.
- **Ví dụ:**
```python
class TrieNode:
    def __init__(self):
        self.children = {}
        self.is_end = False
class Trie:
    def __init__(self):
        self.root = TrieNode()
    def insert(self, word):
        node = self.root
        for c in word:
            if c not in node.children:
                node.children[c] = TrieNode()
            node = node.children[c]
        node.is_end = True
    def search(self, word):
        node = self.root
        for c in word:
            if c not in node.children:
                return False
            node = node.children[c]
        return node.is_end
trie = Trie()
trie.insert("hello")
print(trie.search("hello"))  # True
```

**Two Pointers (Hai con trỏ)**
- **Định nghĩa:** Kỹ thuật dùng hai con trỏ để duyệt mảng/chuỗi, thường dùng cho các bài toán tìm cặp, subarray, đảo ngược.
- **Ưu điểm:** Tối ưu thời gian, giảm độ phức tạp từ O(n^2) xuống O(n), dễ cài đặt.
- **Nhược điểm:** Chỉ áp dụng cho bài toán có tính chất phù hợp (mảng đã sắp xếp, chuỗi liên tục...)
- **Khi nào nên dùng?**
  - Khi cần tìm cặp số, dãy con liên tiếp, hoặc xử lý chuỗi/mảng có tính chất liên tục.
  - Khi muốn tối ưu hóa các bài toán duyệt lồng nhau.
- **Ví dụ:**
```python
# Đảo ngược mảng bằng two pointers
arr = [1,2,3,4,5]
l, r = 0, len(arr)-1
while l < r:
    arr[l], arr[r] = arr[r], arr[l]
    l += 1
    r -= 1
print(arr)
```

---

### 8. Lập trình nâng cao
- **Monotonic Stack/Queue (Ngăn xếp/Hàng đợi đơn điệu)**
- **Line Sweep / Event Sorting (Quét đường, sắp xếp sự kiện)**
- **Binary Search on Answer (Tìm kiếm nhị phân trên đáp án)**
- **Top-K using Heap (Tìm k phần tử lớn nhất/nhỏ nhất bằng Heap)**
- **A* Search (Tìm đường đi ngắn nhất có heuristic)**
- **Math (Toán học: GCD, số nguyên tố, tổ hợp)**

**Monotonic Stack/Queue (Ngăn xếp/Hàng đợi đơn điệu)**
- **Định nghĩa:** Monotonic Stack/Queue là cấu trúc dữ liệu chỉ giữ các phần tử tăng/giảm dần, dùng để giải quyết các bài toán tìm phần tử lớn/nhỏ gần nhất, sliding window max/min.
- **Ưu điểm:** Tối ưu hóa các bài toán O(n^2) xuống O(n), dễ cài đặt với stack/queue.
- **Nhược điểm:** Chỉ áp dụng cho các bài toán có tính chất đơn điệu.
- **Khi nào nên dùng?**
  - Khi cần tìm phần tử lớn/nhỏ gần nhất bên trái/phải, sliding window max/min.
- **Ví dụ:**
```python
# Monotonic Stack: Next Greater Element
nums = [2,1,2,4,3]
stack, res = [], [-1]*len(nums)
for i in range(len(nums)):
    while stack and nums[i] > nums[stack[-1]]:
        res[stack.pop()] = nums[i]
    stack.append(i)
# res = [4,2,4,-1,-1]
```

**Line Sweep / Event Sorting (Quét đường, sắp xếp sự kiện)**
- **Định nghĩa:** Kỹ thuật duyệt các sự kiện theo thứ tự (thường là theo trục x), dùng cho bài toán giao nhau đoạn thẳng, lịch, skyline.
- **Ưu điểm:** Giải quyết hiệu quả các bài toán hình học, lịch, giao nhau.
- **Nhược điểm:** Cần tư duy sắp xếp sự kiện, cài đặt phức tạp hơn duyệt thông thường.
- **Khi nào nên dùng?**
  - Khi cần xử lý các sự kiện theo thứ tự, bài toán giao nhau, lịch, skyline.
- **Ví dụ:**
```python
# Đếm số đoạn giao nhau tại mỗi điểm
intervals = [(1,4),(2,5),(7,9)]
events = []
for s,e in intervals:
    events.append((s,1))
    events.append((e+1,-1))
events.sort()
active, res = 0, []
for x,typ in events:
    active += typ
    res.append((x,active))
print(res)
```

**Binary Search on Answer (Tìm kiếm nhị phân trên đáp án)**
- **Định nghĩa:** Kỹ thuật dùng binary search để tìm giá trị đáp án tối ưu, mỗi lần kiểm tra đáp án bằng một hàm kiểm tra (check function).
- **Ưu điểm:** Tối ưu hóa các bài toán tìm giá trị lớn nhất/nhỏ nhất thỏa mãn điều kiện, giảm độ phức tạp.
- **Nhược điểm:** Chỉ áp dụng cho bài toán có tính chất đơn điệu (có thể kiểm tra được đáp án đúng/sai).
- **Khi nào nên dùng?**
  - Khi cần tìm giá trị tối ưu (min/max) thỏa mãn điều kiện, không biết đáp án cụ thể.
- **Ví dụ:**
```python
# Tìm min k sao cho có thể chia mảng thành <=3 đoạn, mỗi đoạn tổng <=k
arr = [7,2,5,10,8]
left, right = max(arr), sum(arr)
def check(k):
    cnt, cur = 1, 0
    for x in arr:
        if cur + x > k:
            cnt += 1
            cur = 0
        cur += x
    return cnt <= 3
while left < right:
    mid = (left+right)//2
    if check(mid):
        right = mid
    else:
        left = mid+1
print(left)
```

**Top-K using Heap (Tìm k phần tử lớn nhất/nhỏ nhất bằng Heap)**
- **Định nghĩa:** Dùng heap để duy trì k phần tử lớn nhất/nhỏ nhất trong luồng dữ liệu hoặc mảng lớn.
- **Ưu điểm:** Tìm top-k hiệu quả O(n log k), không cần sắp xếp toàn bộ mảng.
- **Nhược điểm:** Không truy cập ngẫu nhiên, chỉ lấy được top-k.
- **Khi nào nên dùng?**
  - Khi cần tìm k phần tử lớn nhất/nhỏ nhất trong mảng lớn hoặc luồng dữ liệu.
- **Ví dụ:**
```python
import heapq
arr = [3,1,4,1,5,9,2,6]
k = 3
print(heapq.nlargest(k, arr))  # 3 phần tử lớn nhất
print(heapq.nsmallest(k, arr)) # 3 phần tử nhỏ nhất
```

**A* Search (Tìm đường đi ngắn nhất có heuristic)**
- **Định nghĩa:** A* là thuật toán tìm đường đi ngắn nhất trên đồ thị có trọng số, sử dụng hàm heuristic để ưu tiên mở rộng các node tiềm năng.
- **Ưu điểm:** Tìm đường đi nhanh hơn Dijkstra khi heuristic tốt, ứng dụng trong AI, game, bản đồ.
- **Nhược điểm:** Cần thiết kế heuristic phù hợp, có thể tốn bộ nhớ nếu không tối ưu.
- **Khi nào nên dùng?**
  - Khi cần tìm đường đi ngắn nhất trên bản đồ, AI, game, bài toán có heuristic tốt.
- **Ví dụ:**
```python
import heapq
# Giả sử heuristic là khoảng cách Manhattan
def astar(start, goal, neighbors, heuristic):
    heap = [(heuristic(start), 0, start)]
    visited = set()
    while heap:
        est, cost, node = heapq.heappop(heap)
        if node == goal:
            return cost
        if node in visited: continue
        visited.add(node)
        for nei, w in neighbors(node):
            if nei not in visited:
                heapq.heappush(heap, (cost+w+heuristic(nei), cost+w, nei))
# Cần cài đặt hàm neighbors và heuristic phù hợp với bài toán cụ thể
```

**Math (Toán học: GCD, số nguyên tố, tổ hợp)**
- **Định nghĩa:** Các kỹ thuật toán học cơ bản như ước chung lớn nhất (GCD), kiểm tra số nguyên tố, tính tổ hợp, chia hết, v.v.
- **Ưu điểm:** Tối ưu hóa các bài toán số học, giảm độ phức tạp, ứng dụng rộng rãi.
- **Nhược điểm:** Cần hiểu rõ lý thuyết toán học, dễ sai nếu không cẩn thận.
- **Khi nào nên dùng?**
  - Khi giải các bài toán về chia hết, số nguyên tố, tổ hợp, xác suất, số học.
- **Ví dụ:**
```python
# GCD
import math
print(math.gcd(12, 18))  # 6
# Kiểm tra số nguyên tố
n = 17
is_prime = n > 1 and all(n%i for i in range(2, int(n**0.5)+1))
print(is_prime)
# Tính tổ hợp C(n, k)
def comb(n, k):
    res = 1
    for i in range(1, k+1):
        res = res * (n-i+1) // i
    return res
print(comb(5,2))  # 10
```

---

## Lời khuyên học tập

1. **Thực hành thường xuyên**
   - Giải ít nhất 1 bài LeetCode mỗi ngày
   - Viết lại code nhiều lần
   - Tối ưu hóa giải pháp

2. **Học theo nhóm**
   - Thảo luận với bạn bè
   - Chia sẻ giải pháp
   - Code review lẫn nhau

3. **Tài nguyên học tập**
   - LeetCode
   - HackerRank
   - GeeksforGeeks
   - YouTube tutorials

## Kết luận

Lộ trình học này được thiết kế để giúp bạn xây dựng nền tảng vững chắc về thuật toán và cấu trúc dữ liệu. Hãy kiên trì và thực hành thường xuyên để đạt được kết quả tốt nhất.

> "Học thuật toán không phải là cuộc chạy nước rút, mà là một cuộc marathon. Hãy kiên trì và đều đặn."

---

[Quay lại: Chương 2 - Tổng quan về phỏng vấn kỹ thuật](../02-technical-interviews/index.md) | [Tiếp theo: Chương 4 - Các chủ đề thuật toán quan trọng](../04-algorithms/index.md) 