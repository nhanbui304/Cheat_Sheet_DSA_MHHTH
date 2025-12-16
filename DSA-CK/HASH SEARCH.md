## 1. So sánh các phương pháp xử lý đụng độ (Hashing)

**Mục tiêu:** Xử lý khi 2 khóa (k_1, k_2) có cùng (h(k)).

| Đặc điểm       | Kết chuỗi (Chaining)                                          | Dò tìm tuyến tính (Linear Probing)                                           | Dò tìm bậc hai (Quadratic Probing)                                                       | Băm đôi (Double Hashing)                                         |
| :------------- | :------------------------------------------------------------ | :--------------------------------------------------------------------------- | :--------------------------------------------------------------------------------------- | :--------------------------------------------------------------- |
| **Cơ chế**     | Mỗi ô chứa 1 danh sách liên kết (Linked List).                | Tìm ô trống kế tiếp: (+1, +2, +3...).                                        | Tìm ô trống theo bình phương: (+1^2, +2^2, +3^2...).                                     | Dùng hàm băm thứ 2 để nhảy: (+1\cdot h_2(k), +2\cdot h_2(k)...). |
| **Công thức**  | (h(k)) xác định Head của List.                                | (index = (h(k) + i) \bmod m)                                                 | (index = (h(k) + i^2) \bmod m) (hoặc (c_1 i + c_2 i^2))                                  | (index = (h_1(k) + i \times h_2(k)) \bmod m)                     |
| **Cấu trúc**   | Ngoài bảng (cần con trỏ phụ).                                 | Trong bảng (tất cả nằm trong array).                                         | Trong bảng.                                                                              | Trong bảng.                                                      |
| **Ưu điểm**    | Xử lý được số lượng phần tử (>) kích thước bảng. Xóa dễ dàng. | Cài đặt đơn giản nhất. Tận dụng tốt bộ nhớ cache (do truy cập tuần tự).      | Giảm được gom cụm chính cấp.                                                             | Phân bố đều nhất. Hạn chế tối đa gom cụm.                        |
| **Nhược điểm** | Tốn bộ nhớ cho con trỏ.                                       | **Gom cụm chính cấp (Primary Clustering)**: Các ô bị lấp đầy dính chùm nhau. | **Gom cụm thứ cấp (Secondary Clustering)**: Các khóa cùng index đầu sẽ đi cùng đường dò. | Tính toán phức tạp hơn (cần 2 hàm băm).                          |
| **Hiệu suất**  | Tốt ngay cả khi bảng đầy ((\alpha > 1)).                      | Giảm mạnh khi bảng gần đầy ((\alpha \to 1)).                                 | Tốt hơn Linear nhưng vẫn giảm khi đầy.                                                   | Tốt nhất trong các loại địa chỉ mở.                              |

---

## 2. So sánh các thuật toán tìm kiếm (Searching)

| Thuật toán                         | Điều kiện tiên quyết         | Độ phức tạp (Time Complexity)            | Khi nào dùng?                                                              | Công thức vị trí (Mở rộng)                                     |
| :--------------------------------- | :--------------------------- | :--------------------------------------- | :------------------------------------------------------------------------- | :------------------------------------------------------------- |
| **Linear Search** (Tuần tự)        | Không cần sắp xếp            | (O(n))                                   | Dữ liệu nhỏ hoặc chưa sắp xếp.                                             | Duyệt từ `0` đến `n-1`.                                        |
| **Binary Search** (Nhị phân)       | **Đã sắp xếp**               | (O(\log n))                              | Dữ liệu lớn, đã sắp xếp. Truy cập ngẫu nhiên (Array).                      | (mid = left + (right - left) / 2)                              |
| **Interpolation Search** (Nội suy) | Đã sắp xếp + **Phân bố đều** | TB: (O(\log(\log n)))<br>Tệ nhất: (O(n)) | Dữ liệu số học, phân bố đều (ví dụ: danh bạ điện thoại, từ điển).          | (pos = lo + \dfrac{hi - lo}{A[hi] - A[lo]} \times (x - A[lo])) |
| **Jump Search** (Bước nhảy)        | Đã sắp xếp                   | (O(\sqrt{n}))                            | Khi chi phí quay lui (backward) cao. Tìm block chứa (x) rồi Linear search. | Bước nhảy (m = \sqrt{n}).                                      |

---

## 3. Tổng hợp công thức & Mẹo thi (Kiến thức mở rộng)

### A. Về Bảng Băm

1. **Hệ số tải (Load Factor – (\alpha)):**

   * (\alpha = \dfrac{n}{m})
     ((n): số phần tử, (m): kích thước bảng).
   * Với **Địa chỉ mở**, (\alpha \le 1).
   * Với **Kết chuỗi**, (\alpha) có thể (> 1).

2. **Quy tắc xóa trong Địa chỉ mở:**

   * Không được xóa “trắng” (set về `NULL`) vì sẽ làm đứt mạch dò.
   * **Giải pháp:** dùng cờ `DELETED` hoặc `AVAILABLE`.

3. **Lưu ý về Double Hashing:**

   * (h_2(k) \ne 0) (nếu bằng 0 → đứng yên, lặp vô hạn).
   * Thường chọn (m) là **số nguyên tố** để chuỗi dò đi qua toàn bộ bảng.

---

### B. Về Tìm Kiếm

1. **Binary Search – tránh tràn số:**

   * ❌ Sai: `mid = (left + right) / 2`
   * ✅ Đúng: `mid = left + (right - left) / 2`

2. **Interpolation Search:**

   * Rất tệ ((O(n))) nếu dữ liệu phân bố lệch
     (ví dụ: (1,2,4,8,16...)).
   * Chỉ dùng khi dữ liệu tăng **gần tuyến tính đều**
     (ví dụ: (10,20,30,40...)).

3. **So sánh nhanh (trung bình):**

   * **Interpolation > Binary > Jump > Linear** (với dữ liệu “đẹp”).
