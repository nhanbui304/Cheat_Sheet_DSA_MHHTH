
# HEAP – CHEAT SHEET TỔNG HỢP ĐẦY ĐỦ (DÙNG ÔN THI)

## I. Bộ Công Thức Toán & Index (RẤT QUAN TRỌNG)

⚠️ **Luôn phân biệt đề bài dùng chỉ số bắt đầu từ 0 hay từ 1.**
Tài liệu của bạn và chuẩn C/C++ dùng **0-based index**.

---

## 1. Binary Heap (Heap nhị phân – mỗi node tối đa 2 con)

| Loại công thức                 | Index bắt đầu từ 0 (Chuẩn C++) | Index bắt đầu từ 1 (Pseudo-code) |
| ------------------------------ | ------------------------------ | -------------------------------- |
| **Node đang xét**              | `i`                            | `i`                              |
| **Node Cha (Parent)**          | ⌊(i − 1) / 2⌋                  | ⌊i / 2⌋                          |
| **Con Trái (Left Child)**      | `2i + 1`                       | `2i`                             |
| **Con Phải (Right Child)**     | `2i + 2`                       | `2i + 1`                         |
| **Điều kiện tồn tại Con Trái** | `2i + 1 < heap_size`           | `2i ≤ heap_size`                 |
| **Điều kiện tồn tại Con Phải** | `2i + 2 < heap_size`           | `2i + 1 ≤ heap_size`             |
| **Vị trí node Lá (Leaf)**      | từ ⌊n / 2⌋ đến `n − 1`         | từ ⌊n / 2⌋ + 1 đến `n`           |
| **Node Không-Phải-Lá**         | từ `0` đến ⌊n / 2⌋ − 1         | từ `1` đến ⌊n / 2⌋               |

---

## 2. K-ary Heap (Heap k-ary / d-ary)

Áp dụng cho **3-ary heap**, **4-ary heap**, …

* **Node đang xét:** `i` (0-based)
* **Node Cha:** ⌊(i − 1) / k⌋
* **Con thứ j (1 ≤ j ≤ k):** `k·i + j`
* **Chiều cao Heap:**
  [
  h = \lfloor \log_k n \rfloor
  ]
  (Binary Heap là trường hợp k = 2)

---

## 3. Công thức về Chiều cao & Số lượng Node

Giả sử Heap có `n` phần tử, gốc ở độ sâu 0:

* **Chiều cao Heap:**
  [
  h = \lfloor \log_2 n \rfloor
  ]

* **Số node tối đa ở mức h:**
  [
  2^h
  ]

* **Tổng số node tối đa của cây cao h:**
  [
  2^{h+1} - 1
  ]

* **Khoảng giá trị n theo chiều cao:**
  [
  2^h \le n \le 2^{h+1} - 1
  ]

* **Độ sâu node sâu nhất:**
  [
  \lfloor \log_2 n \rfloor
  ]

---

## II. Bảng Độ Phức Tạp (Time Complexity)

| Thao tác                    | Độ phức tạp | Ghi chú                 |
| --------------------------- | ----------- | ----------------------- |
| **Get Top (Min/Max)**       | O(1)        | Chỉ truy cập `arr[0]`   |
| **Heapify (Reheap Down)**   | O(log n)    | Cho 1 node bị sai       |
| **Insert**                  | O(log n)    | Thêm cuối + Reheap Up   |
| **Remove (Xóa Root)**       | O(log n)    | Swap đầu–cuối + Heapify |
| **Build Heap (tối ưu)**     | **O(n)**    | Heapify từ ⌊n/2⌋ − 1    |
| **Build Heap (Insert dần)** | O(n log n)  | Không tối ưu            |
| **Heap Sort**               | O(n log n)  | Luôn cố định            |
| **Tìm phần tử bất kỳ**      | O(n)        | Không hỗ trợ tìm nhanh  |
| **Gộp 2 Heap size n**       | O(n)        | Nối mảng + Build Heap   |

---

## III. Các Dạng Bài Tập & Cách Giải

### Dạng 1: Cho mảng → hỏi kết quả sau khi Build Heap

**Cách giải chuẩn (O(n))**

1. Bắt đầu từ `i = ⌊n/2⌋ − 1`
2. Duyệt ngược về `0`
3. Mỗi `i` thực hiện **Heapify Down**

⚠️ **Không dùng Insert từng phần tử** nếu đề không yêu cầu rõ.

---

### Dạng 2: Insert / Remove trên Heap

**Insert**

* Thêm vào vị trí trống tiếp theo
* **So sánh với CHA**
* Thực hiện **Reheap Up**

**Remove (Root)**

* Lấy node lá cuối lên gốc
* Xóa node lá
* **So sánh với CON**
* Thực hiện **Heapify Down**

💡 *Mẹo thi:* vẽ cây → nhanh và ít sai hơn nhìn mảng.

---

### Dạng 3: Kiểm tra mảng có phải Heap không

**Thuật toán**

1. Duyệt `i` từ `0` đến `⌊n/2⌋ − 1`
2. Kiểm tra cha–con

**Min-Heap**

```
arr[i] ≤ arr[2i+1] và arr[i] ≤ arr[2i+2]
```

**Max-Heap**

```
arr[i] ≥ arr[2i+1] và arr[i] ≥ arr[2i+2]
```

Chỉ cần sai 1 cặp → **không phải Heap**

---

### Dạng 4: Điền code / Tìm lỗi sai

**Reheap Up**

```cpp
while (i > 0 && arr[i] > arr[(i-1)/2]) {
    swap(arr[i], arr[(i-1)/2]);
    i = (i-1)/2;
}
```

**Heapify Down**

* Tính `left`, `right`
* **BẮT BUỘC:** kiểm tra chỉ số < heap_size
* Tìm `largest` hoặc `smallest`
* Swap → gọi heapify tiếp

---

### Dạng 5: Bài toán ứng dụng

**K phần tử lớn nhất / nhỏ nhất**

* Build Heap O(n)
* Pop K lần → O(K log n)
* Tổng: **O(n + K log n)**

**Heap kích thước K** (dữ liệu rất lớn)

* Giữ heap size K
* Duyệt mảng → tối ưu bộ nhớ

**Tổng ≤ M**

* Luôn lấy Root
* Cộng dồn
* Pop tiếp nếu còn ≤ M

---

### Dạng 6: 3-ary Heap (Heap 3 con)

* **Parent:** `(i−1)/3`
* **Con:** `3i+1`, `3i+2`, `3i+3`
* Heapify: so sánh CHA với **3 CON**

---

## IV. Các Bẫy RẤT HAY RA THI

1. **Nhầm Reheap Up và Heapify**

   * Insert → **Up**
   * Delete / Build → **Down**

2. **Nhầm Min-Heap và Max-Heap**

   * Đọc kỹ dấu so sánh

3. **Nhầm số phần tử và chỉ số**

   * N phần tử → chỉ số `0..N−1`
   * Điều kiện thường là `< N`

4. **Bug nguy hiểm**

```cpp
parent = (i-1)/2;
```

Nếu không check `i > 0` → **vòng lặp vô hạn**
