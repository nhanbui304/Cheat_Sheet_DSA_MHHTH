
# TREE (CÂY) – CHEAT SHEET ÔN THI

## I. Các Công Thức “SỐNG CÒN” (Binary Tree)

⚠️ Luôn kiểm tra đề bài quy ước **chiều cao / mức bắt đầu từ 0 hay 1**.
Thông thường: **gốc ở mức 1, chiều cao = số tầng**.

---

### 1. Công thức cơ bản

* **Số node tối đa** của cây có chiều cao (h):
  [
  N_{\max} = 2^h - 1
  ]

* **Số node tối thiểu** của cây có chiều cao (h):
  [
  N_{\min} = h \quad (\text{cây lệch / suy biến})
  ]

* **Chiều cao nhỏ nhất** để chứa (N) node:
  [
  H_{\min} = \lfloor \log_2 N \rfloor + 1
  ]
  hoặc
  [
  H_{\min} = \lceil \log_2 (N+1) \rceil
  ]

* **Chiều cao lớn nhất** với (N) node:
  [
  H_{\max} = N
  ]

---

### 2. Node lá (Leaf)

* **Cây nhị phân đầy đủ:**
  [
  \text{Số lá} = \frac{N + 1}{2}
  ]

* **Tổng quát:**
  [
  n_0 = n_2 + 1
  ]
  (số node bậc 0 luôn hơn số node bậc 2 đúng 1)

---

## II. Các Loại Cây & Đặc Điểm Cốt Lõi

---

### 1. Binary Search Tree (BST)

**Quy tắc:**
[
\text{Con trái} < \text{Gốc} < \text{Con phải}
]

**Tính chất vàng (RẤT HAY RA):**

* Duyệt **In-order (LNR)** → dãy **tăng dần**

**Độ phức tạp:**

* Trung bình: (O(\log N))
* Xấu nhất (cây lệch): (O(N))

---

### 2. AVL Tree (Cây cân bằng)

* Là **BST + điều kiện cân bằng**
  [
  |height_{left} - height_{right}| \le 1
  ]

* **Balance Factor:** chỉ nằm trong ([-1, 1])

* **Độ phức tạp (luôn đảm bảo):**

  * Insert / Delete / Search: (O(\log N))

---

### 3. B-Tree (Cây đa nhánh)

Dùng cho **lưu trữ ngoài, CSDL lớn**.

* **Bậc m:**

  * Tối đa **m con**
  * Tối đa **m − 1 khóa**

* **Node trong (trừ gốc):**

  * Ít nhất (\lceil m/2 \rceil) con

* **Tất cả node lá nằm cùng mức**

* **Split node:** xảy ra khi chèn vào node đã đầy

---

## III. Phép Duyệt Cây (Traversals) – CỰC QUAN TRỌNG

### 1. Thứ tự duyệt

* **Pre-order:** **N**LR
  → Node đầu tiên luôn là **Gốc**

* **Post-order:** LR**N**
  → Node cuối cùng luôn là **Gốc**

* **In-order:** L**N**R
  → Xác định **biên trái – phải** của gốc

---

### 2. Dựng cây từ 2 dãy duyệt

**Quy trình chuẩn:**

1. Dùng:

   * **Pre-order:** lấy phần tử **đầu**
   * **Post-order:** lấy phần tử **cuối**
     → xác định `root`

2. Tìm `root` trong **In-order**

   * Bên trái → cây con trái
   * Bên phải → cây con phải

3. Đệ quy cho từng phần

⚠️ **Không thể dựng cây duy nhất nếu chỉ có Pre + Post** (thi hay hỏi bẫy).

---

## IV. AVL – Các Trường Hợp Quay (Rotations)

Xét node mất cân bằng `grandParent`.

---

### 1. Lệch Trái – Trái (LL)

* Node mới nằm **trái của con trái**
* → **Quay phải** tại `grandParent`

---

### 2. Lệch Phải – Phải (RR)

* Node mới nằm **phải của con phải**
* → **Quay trái** tại `grandParent`

---

### 3. Lệch Trái – Phải (LR)

* Node mới nằm **phải của con trái**
* → Quay trái ở **con trái**
* → Quay phải ở `grandParent`

---

### 4. Lệch Phải – Trái (RL)

* Node mới nằm **trái của con phải**
* → Quay phải ở **con phải**
* → Quay trái ở `grandParent`

---

### Code mẫu: Rotate Right

```cpp
Node* rotateRight(Node* y) {
    Node* x = y->left;
    y->left = x->right;
    x->right = y;
    return x;
}
```

---

## V. Lỗi Sai & Bẫy RẤT HAY GẶP

### 1. Nhầm khái niệm

* **Full Binary Tree:**
  Mỗi node có **0 hoặc 2 con**

* **Complete Binary Tree:**
  Lấp đầy từ trên xuống, trái sang phải

⚠️ **AVL không nhất thiết là Complete**

---

### 2. Xóa node có 2 con trong BST

Phải thay bằng:

* **Max của cây con trái**
* **Hoặc Min của cây con phải**

⚠️ Đề thường **cố định cách xóa** → đọc kỹ.

---

### 3. Expression Tree (Cây biểu thức)

* Prefix → Pre-order
* Infix → In-order (thêm ngoặc)
* Postfix → Post-order

**Mẹo nhanh:**
Infix → Postfix bằng **Stack**, toán tử ưu tiên cao hơn hoặc bằng thì pop.

---

### 4. Splay Tree

* Mỗi lần truy cập → **bắt buộc splay lên gốc**
* Truy cập tăng dần → cây biến thành danh sách (O(N))

---

## VI. Mẹo Làm Trắc Nghiệm Nhanh

1. **Thử giá trị nhỏ** (N = 1, 2, 3) để loại đáp án.
2. **Vẽ nháp** khi gặp AVL, xóa BST.
3. **BST + In-order:** phải tăng dần → sai là loại ngay.
4. **Đếm lá:**
   [
   N = \text{node nội} + \text{node lá}
   ]

---