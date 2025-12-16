
###1. Phân loại & Nhận biết Đồ thị (Quan trọng cho trắc nghiệm)Ngoài đồ thị vô hướng/có hướng cơ bản, bạn cần nắm vững:

* **Đồ thị Hai phía (Bipartite Graph):**
* **Định nghĩa:** Có thể chia tập đỉnh thành 2 tập U, V rời nhau sao cho mọi cạnh đều nối 1 đỉnh thuộc U với 1 đỉnh thuộc V.
* **Mẹo nhận biết:** Dùng BFS/DFS để tô màu (2 màu). Nếu gặp cạnh nối 2 đỉnh cùng màu \rightarrow Không phải hai phía.
* **Tính chất:** Đồ thị hai phía **không chứa chu trình lẻ**.


* **Đồ thị Euler (Vẽ một nét):**
* **Chu trình Euler:** Đi qua tất cả các **cạnh**, mỗi cạnh đúng 1 lần và quay về nơi xuất phát.
* **Điều kiện (Vô hướng):** Đồ thị liên thông + **Tất cả các đỉnh đều có bậc chẵn**.
* **Đường đi Euler:** Đi qua hết cạnh nhưng không cần quay về. Điều kiện: Có đúng **0 hoặc 2 đỉnh bậc lẻ**.


* **Đồ thị Hamilton:**
* **Chu trình Hamilton:** Đi qua tất cả các **đỉnh**, mỗi đỉnh đúng 1 lần.
* **Lưu ý:** Bài toán tìm chu trình Hamilton là bài toán khó (NP-Complete), thường đề chỉ hỏi trên đồ thị nhỏ hoặc đồ thị đặc biệt.


* **Cây (Tree):**
* Là đồ thị vô hướng, liên thông, không chu trình.
* Số cạnh luôn là E = V - 1.
* Giữa 2 đỉnh bất kỳ luôn có duy nhất 1 đường đi.



---

###2. Mở rộng Thuật toán Tìm đường đi ngắn nhấtKhông chỉ có Dijkstra, bạn cần biết khi nào dùng cái gì:

| Thuật toán | Đặc điểm | Độ phức tạp | Khi nào dùng? |
| --- | --- | --- | --- |
| **BFS** | Trọng số các cạnh bằng nhau (hoặc không trọng số). | O(V+E) | Tìm đường đi ít cạnh nhất. |
| **Dijkstra** | Trọng số **không âm** (\ge 0). | O(E \log V) | Chuẩn mực cho đồ thị trọng số dương. |
| **Bellman-Ford** | Chấp nhận **trọng số âm**. | O(V \cdot E) | Khi đồ thị có cạnh âm. Phát hiện được **chu trình âm**. |
| **Floyd-Warshall** | Tìm đường đi giữa **mọi cặp đỉnh**. | O(V^3) | Khi V nhỏ (V < 400). Dùng Quy hoạch động. |

**Công thức Floyd-Warshall (3 vòng for lồng nhau):**


---

###3. Thành phần Liên thông & Cấu trúc đồ thị (Advanced DFS)Phần này dùng DFS cực nhiều để phân tích sâu cấu trúc đồ thị:

* **Cầu (Bridge):** Là cạnh mà nếu xóa đi, số thành phần liên thông tăng lên (đồ thị bị đứt đôi).
* **Khớp (Articulation Point):** Là đỉnh mà nếu xóa đi (cùng các cạnh kề), số thành phần liên thông tăng lên.
* *Thuật toán:* Dùng `low[u]` và `num[u]` (thứ tự thăm) trong DFS.


* **Thành phần liên thông mạnh (SCC - Strongly Connected Components):**
* Chỉ xét trên **đồ thị có hướng**.
* Là tập hợp các đỉnh mà từ bất kỳ đỉnh nào cũng đi tới được các đỉnh còn lại trong tập đó.
* *Thuật toán:* **Tarjan** hoặc **Kosaraju** (Thường Tarjan nhanh và gọn hơn, O(V+E)).



---

###4. Phát hiện Chu trình (Cycle Detection) - Chi tiết* **Trên đồ thị Vô hướng:**
* Dùng DFS/BFS. Nếu gặp một đỉnh `v` đã thăm mà `v` không phải là cha trực tiếp (parent) của đỉnh đang xét `u` \rightarrow Có chu trình.
* Dùng **DSU (Disjoint Set Union)**: Khi thêm cạnh (u, v), nếu u và v đã cùng chung một tập hợp cha \rightarrow Có chu trình.


* **Trên đồ thị Có hướng:**
* Dùng DFS với **3 màu** (Trắng: chưa thăm, Xám: đang thăm dở dang trong stack đệ quy, Đen: đã thăm xong).
* Nếu gặp một đỉnh màu **Xám** \rightarrow Có chu trình (Back edge).



---

###5. Cây Khung (Spanning Tree) - So sánh Prim vs KruskalĐể tìm Cây khung nhỏ nhất (MST):

* **Kruskal:**
* Tư duy: Xếp cạnh từ nhỏ đến lớn, nhặt từng cạnh vào, dùng DSU để tránh tạo vòng.
* Tốt cho: **Đồ thị thưa** (Sparse Graph - ít cạnh).
* Code dễ hơn.


* **Prim:**
* Tư duy: Giống Dijkstra. Xuất phát từ 1 đỉnh, loang dần ra bằng cách chọn cạnh nhỏ nhất nối từ tập đã thăm ra tập chưa thăm.
* Tốt cho: **Đồ thị dày** (Dense Graph - nhiều cạnh, E \approx V^2).



---

###6. Mẹo nhớ nhanh để "cứu cánh" trong phòng thi1. **Ma trận kề vs Danh sách kề:**
* Ma trận kề tốn bộ nhớ V^2 \rightarrow Chỉ dùng khi V nhỏ (vài trăm). Check cạnh (u, v) mất O(1).
* Danh sách kề tốn V+E \rightarrow Dùng cho V lớn (10^5). Check cạnh (u, v) có thể mất O(deg(u)).


2. **Topological Sort (Sắp xếp Topo):**
* Chỉ áp dụng cho **DAG** (Có hướng, Không chu trình). Nếu đồ thị có chu trình, thuật toán sẽ không trả về đủ V đỉnh. \rightarrow Đây cũng là cách kiểm tra chu trình.


3. **Đường đi ngắn nhất trên DAG:**
* Có thể tìm được trong O(V+E) bằng cách Sắp xếp Topo trước, sau đó duyệt tuyến tính (Relax) theo thứ tự Topo. Nhanh hơn Dijkstra.



###Tóm lại: Sơ đồ tư duy khi gặp bài toán Đồ thị1. **Đọc đề:** Có hướng hay vô hướng? Có trọng số hay không? Trọng số âm hay dương?
2. **Kích thước:**
* V \le 20: Có thể dùng đệ quy quay lui trâu bò, hoặc bitmask.
* V \le 400: Floyd-Warshall (O(V^3)), Ma trận kề.
* V \le 1000: Dijkstra O(V^2) (không cần Heap).
* V \le 10^5: Danh sách kề + BFS/DFS/Dijkstra (Heap).


3. **Yêu cầu:**
* *Liên thông?* \rightarrow DFS/BFS/DSU.
* *Ngắn nhất?* \rightarrow BFS (không trọng số), Dijkstra (trọng số +).
* *Thứ tự trước sau?* \rightarrow Topo Sort.
* *MST?* \rightarrow Kruskal.