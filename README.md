# Cheat-Sheet-Mo-Hinh-Hoa



## Dạng 1: Tìm số điểm cực biên (Extreme Points) TỐI ĐA

Dạng này thường hỏi về một bài toán QHTT _chưa_ ở dạng chuẩn (còn dùng bất phương trình $\le$ hoặc $\ge$).

-   **Tham số:**
    
    -   $n$: Số biến
        
    -   $m$: Số ràng buộc chính (bất phương trình)
        
-   **Giải thích:** Một điểm cực biên là giao điểm của $n$ mặt phẳng (ràng buộc). Tổng số các mặt phẳng ràng buộc là $m$ (ràng buộc chính) + $n$ (ràng buộc không âm $x_i \ge 0$).
    
-   Công thức (cho số TỐI ĐA):
    
    $$\text{Số điểm tối đa} = \binom{m+n}{n}$$
    
-   **Ví dụ (Câu đầu tiên):** $n=3$ biến, $m=6$ ràng buộc chính.
    
    -   Kết quả: $\binom{6+3}{3} = \binom{9}{3} = 84$.
        

----------

## Dạng 2: Tìm tổng số nghiệm cơ bản (Basic Solutions)

Dạng này thường hỏi về một bài toán QHTT _đã_ ở dạng chuẩn (chỉ dùng phương trình $=$).

-   **Tham số:**
    
    -   $n$: Tổng số biến
        
    -   $m$: Số phương trình ràng buộc
        
-   **Phương pháp làm (Quan trọng):**
    
    1.  **Bước 1:** Xác định $n$ và $m$.
        
    2.  **Bước 2:** Kiểm tra **hạng (rank) của ma trận hệ số $A$**. Gọi hạng là $r$. Đây là bước mấu chốt để không bị lừa. $r$ chính là số phương trình _độc lập tuyến tính_ thực sự.
        
        -   Nếu các phương trình độc lập $\implies r = m$.
            
        -   Nếu có phương trình thừa (phụ thuộc tuyến tính) $\implies r < m$.
            
    3.  **Bước 3:** Số nghiệm cơ bản là số cách chọn $r$ biến cơ sở từ $n$ tổng số biến.
        
-   Công thức (Chung):
    
    $$\text{Số nghiệm cơ bản} = \binom{n}{r}$$
    
-   **Ví dụ (Câu thứ hai):** $n=6$ biến, $m=3$ phương trình.
    
    -   _Kiểm tra (Bước 2):_ Phát hiện 1 phương trình là tổ hợp của 2 phương trình còn lại.
        
    -   _Hạng thực sự:_ $r = 2$.
        
    -   _Kết quả (Bước 3):_ $\binom{n}{r} = \binom{6}{2} = 15$.


## Dạng 3: tìm số nghiệm cơ bản khả thi tối ưu

Đây là phương pháp chung để tìm **"Số nghiệm cơ bản khả thi tối ưu"**:

Mục tiêu là tìm các _đỉnh_ của miền khả thi (gọi là Nghiệm cơ bản khả thi - BFS) mà tại đó hàm mục tiêu $Z$ đạt giá trị tốt nhất (max hoặc min).

----------

## Các bước làm chung

1.  **Xác định $n$ và $m$:**
    
    -   $n$ = Tổng số biến (ví dụ: $x_1, x_2, x_3, x_4 \implies n=4$).
        
    -   $m$ = Số phương trình ràng buộc (ví dụ: có 2 phương trình $\implies m=2$).
        
    -   _(Kiểm tra nhanh xem $m$ phương trình có độc lập không. Thường là có)._
        
2.  **Tính số nghiệm cơ bản (BS) tối đa:**
    
    -   Số nghiệm cơ bản = $\binom{n}{m}$.
        
    -   Đây là tổng số "tổ hợp cơ sở" (các giao điểm) bạn cần kiểm tra.
        
    -   Ví dụ: $\binom{4}{2} = 6$ nghiệm cơ bản.
        
3.  **Lập bảng và kiểm tra từng nghiệm cơ bản (BS):**
    
    -   Kẻ một bảng để liệt kê tất cả $\binom{n}{m}$ trường hợp. Mỗi trường hợp là một "cơ sở" (tập hợp $m$ biến). Các biến còn lại ($n-m$ biến) sẽ cho bằng 0.
        
    -   **Cột 1: Cơ sở (Các biến được chọn):** Ví dụ $\{x_1, x_2\}$.
        
    -   **Cột 2: Giải hệ phương trình:** Cho các biến _không_ thuộc cơ sở bằng 0 (ví dụ $x_3=0, x_4=0$) và giải hệ $m$ phương trình để tìm giá trị của các biến cơ sở.
        
    -   **Cột 3: Nghiệm cơ bản (BS):** Ghi lại nghiệm đầy đủ, ví dụ: $(4, 1, 0, 0)$.
        
    -   **Cột 4: Kiểm tra khả thi (Tìm BFS):** Kiểm tra xem tất cả các thành phần của nghiệm có $\ge 0$ không.
        
        -   Nếu có $\implies$ Đây là một **Nghiệm cơ bản khả thi (BFS)**.
            
        -   Nếu có dù chỉ 1 số âm $\implies$ Loại (Không khả thi).
            
    -   **Cột 5: Tính $Z$ (Nếu khả thi):** Chỉ tính giá trị hàm mục tiêu $Z$ cho những nghiệm **BFS** (ở Cột 4).
        
4.  **Kết luận:**
    
    -   Nhìn vào tất cả các giá trị $Z$ ở Cột 5.
        
    -   Tìm giá trị $Z$ tối ưu (nhỏ nhất nếu bài toán `min`, lớn nhất nếu bài toán `max`).
        
    -   **Đếm số lượng BFS** có cùng giá trị $Z$ tối ưu đó.
        


----------

# Bài toán Phân công (Assignment Problem)

### 1. Mô tả bài toán 🎯

Đây là bài toán tìm cách gán $n$ "tác nhân" (ví dụ: công nhân, máy móc) cho $n$ "nhiệm vụ" (ví dụ: công việc) sao cho:

-   **Một-đối-một:** Mỗi tác nhân chỉ làm _đúng một_ nhiệm vụ.
    
-   **Một-đối-một:** Mỗi nhiệm vụ chỉ được giao cho _đúng một_ tác nhân.
    
-   **Tối ưu:** Tổng chi phí (hoặc thời gian) là **nhỏ nhất (Minimize)**, hoặc tổng lợi nhuận là **lớn nhất (Maximize)**.
    

Đây là một trường hợp đặc biệt của **Bài toán vận tải (Transportation Problem)**.

### 2. Mô hình toán học (Dạng chuẩn: Minimize) 📐

**a. Dữ liệu đầu vào:**

-   $n$: Số lượng tác nhân (và cũng là số lượng nhiệm vụ).
    
-   $C = [c_{ij}]$: Ma trận chi phí, trong đó $c_{ij}$ là chi phí để tác nhân $i$ thực hiện nhiệm vụ $j$.
    

**b. Biến quyết định:**

-   $x_{ij}$: Biến nhị phân (0 hoặc 1).
    
    -   $x_{ij} = 1$ nếu tác nhân $i$ được gán cho nhiệm vụ $j$.
        
    -   $x_{ij} = 0$ nếu không.
        

**c. Hàm mục tiêu (Minimize Cost):**

Tìm cách gán sao cho tổng chi phí là nhỏ nhất.

$$\text{Minimize } Z = \sum_{i=1}^{n} \sum_{j=1}^{n} c_{ij} x_{ij}$$

**d. Ràng buộc (Constraints):**

1.  Mỗi tác nhân $i$ chỉ làm 1 nhiệm vụ: (Tính tổng theo cột - theo $j$)
    
    $$\sum_{j=1}^{n} x_{ij} = 1 \quad (\text{với mọi } i = 1, \dots, n)$$
    
    (Đây chính là đáp án B trong câu hỏi của bạn)
    
2.  Mỗi nhiệm vụ $j$ chỉ được giao cho 1 tác nhân: (Tính tổng theo hàng - theo $i$)
    
    $$\sum_{i=1}^{n} x_{ij} = 1 \quad (\text{với mọi } j = 1, \dots, n)$$
    
    (Đây là đáp án A trong câu hỏi của bạn)
    
3.  Điều kiện của biến:
    
    $$x_{ij} \in \{0, 1\} \quad (\text{với mọi } i, j)$$
    
    (Lưu ý: Trong thực tế, chỉ cần $x_{ij} \ge 0$ là đủ. Do tính chất đặc biệt của bài toán này, khi giải bằng Quy hoạch tuyến tính, nghiệm tối ưu luôn tự động là số nguyên 0 hoặc 1).
    


### 3. Các biến thể thường gặp 🔄

**a. Bài toán không cân bằng (Unbalanced):**

-   **Tình huống:** Số tác nhân $m \neq$ số nhiệm vụ $n$.
    
-   **Giải pháp:** Thêm "tác nhân giả" (dummy agent) hoặc "nhiệm vụ giả" (dummy task) để ma trận trở thành vuông ($n \times n$).
    
-   **Chi phí:** Gán chi phí $c_{ij} = 0$ cho tất cả các ô "giả" này (để chúng không ảnh hưởng đến hàm mục tiêu).
    

**b. Bài toán tìm Lợi nhuận lớn nhất (Maximization):**

-   **Tình huống:** $c_{ij}$ là lợi nhuận, cần tìm $\text{Maximize } Z = \sum \sum c_{ij} x_{ij}$.
    
-   Giải pháp (Cách 1): Đổi dấu hàm mục tiêu.
    
    $$\text{Maximize } Z \Longleftrightarrow \text{Minimize } (-Z) = \sum \sum (-c_{ij}) x_{ij}$$
    
    (Giải bài toán Minimize với ma trận chi phí mới là $-c_{ij}$)
    
-   **Giải pháp (Cách 2):** Tạo ma trận "tiếc nuối" (regret matrix).
    
    1.  Tìm $M$, giá trị lớn nhất trong toàn bộ ma trận $C$.
        
    2.  Tạo ma trận chi phí mới $c'_{ij} = M - c_{ij}$.
        
    3.  Giải bài toán Minimize với ma trận $C'$ này.
        

**c. Phân công bị cấm:**

-   **Tình huống:** Tác nhân $i$ _không thể_ làm nhiệm vụ $j$.
    
-   **Giải pháp:** Gán chi phí cho ô đó $c_{ij} = \infty$ (hoặc một số $M$ rất lớn) để thuật toán tự động "tránh" chọn ô này.
    
----------

## 1. Phương pháp Đơn hình (Simplex Method)

-   **Biến cơ sở (Basic Variable):**
    
    -   Chi phí rút gọn (Reduced Cost) **luôn bằng 0**. (Câu 13)
        
    -   Trong bảng đơn hình, giá trị của chúng được đọc ở cột RHS (vế phải).
        
-   **Biến phi cơ sở (Non-basic Variable):**
    
    -   Giá trị (Value) của chúng **luôn bằng 0**. (Câu 20)
        
    -   Chi phí rút gọn của chúng (hàng $Z_j - C_j$ hoặc $\Delta$) cho biết tính tối ưu.
        
-   **Nghiệm cơ sở (Basic Solution):**
    
    -   Tìm bằng cách cho $n-m$ biến (phi cơ sở) bằng 0 và giải hệ $m$ phương trình cho $m$ biến còn lại. (Câu 32)
        
    -   Nghiệm cơ sở có thể **không khả thi** (not feasible) nếu có giá trị âm. (Câu 20)
        
-   **Nghiệm cơ sở khả thi (BFS):**
    
    -   Là một nghiệm cơ sở mà tất cả các biến $\ge 0$. (Câu 33)
        
    -   Thuật toán Đơn hình di chuyển giữa các BFS.
        
-   **Điều kiện tối ưu (Dừng thuật toán):** (Câu 35)
    
    1.  **Khả thi:** Cột vế phải (RHS) $\ge 0$. (Câu 34)
        
    2.  **Tối ưu:** Hàng chi phí rút gọn thỏa mãn:
        
        -   **Bài toán MIN:** Tất cả chi phí rút gọn $\ge 0$.
            
        -   **Bài toán MAX:** Tất cả chi phí rút gọn $\le 0$.
            
-   **Dấu hiệu nghiệm không bị chặn (Unbounded):** (Câu 19)
    
    -   Khi đã chọn cột trụ (biến đi vào), nhưng **tất cả hệ số trong cột đó đều $\le 0$**.
        
    -   Điều này có nghĩa là không thể thực hiện phép thử tỉ lệ (ratio test) để chọn dòng trụ.
        
-   **Kiểm tra một điểm có phải BFS tối ưu không:** (Câu 18)
    
    1.  **Kiểm tra Khả thi:** Thay điểm vào _tất cả_ ràng buộc (bao gồm $x_i \ge 0$). Phải thỏa mãn hết.
        
    2.  **Kiểm tra Cơ sở:** Các biến $> 0$ là biến cơ sở, biến $= 0$ là phi cơ sở. Ma trận cột $A$ ứng với các biến cơ sở phải khả nghịch (độc lập tuyến tính).
        
    3.  **Kiểm tra Tối ưu (cho bài MIN):** Tính chi phí rút gọn $\bar{c}_j = c_j - c_B^T B^{-1} A_j$ cho _tất cả các biến phi cơ sở_. Nếu tất cả $\bar{c}_j \ge 0$ thì là tối ưu.
        

----------

## 2. Lý thuyết Quy hoạch tuyến tính (LP)

-   **Định lý cơ bản:** Nếu một bài toán QHTT có nghiệm tối ưu, thì **ít nhất một** nghiệm tối ưu phải nằm tại **đỉnh (corner/vertex)** của miền khả thi. (Câu 14 - ý I)
    
-   **Nghiệm tối ưu:**
    
    -   **Không bao giờ** nằm _bên trong_ miền khả thi. (Câu 14 - ý III)
        
    -   Có thể nằm trên _cạnh_ (không phải đỉnh) nếu có vô số nghiệm tối ưu. (Câu 14 - ý II sai)
        
-   **Phép biến đổi:** $\min(Z)$ tương đương với $\max(-Z)$. (Câu 31)
    

----------

## 3. Nhánh và Cận (Branch and Bound - B&B)

-   **Mục đích:** Giải bài toán Quy hoạch _nguyên_ (Integer Programming).
    
-   **Bước đầu tiên (Nút gốc):** (Câu 2, 30)
    
    -   **Nới lỏng tuyến tính (LP Relaxation):** Bỏ (drop) ràng buộc $x$ phải là số nguyên.
        
    -   Giải bài toán QHTT nới lỏng đó để có cận đầu tiên (ví dụ: Cận trên $UB$ cho bài toán MAX).
        
-   **Các cận (cho bài toán MAX):**
    
    -   **Cận trên (Upper Bound - UB):** Giá trị của nghiệm nới lỏng LP (luôn $\ge$ nghiệm nguyên tốt nhất).
        
    -   **Cận dưới (Lower Bound - LB):** Giá trị của nghiệm _nguyên_ khả thi tốt nhất tìm được cho đến nay.
        
-   **Quy tắc cắt tỉa (Dừng nhánh):** (Câu 28)
    
    -   Dừng nhánh (không xét tiếp) khi:
        
        1.  **Cận trên $\le$ Cận dưới ($UB \le LB$):** Nhánh này không có khả năng cho nghiệm tốt hơn nghiệm nguyên đã tìm thấy.
            
        2.  Bài toán nới lỏng tại nút đó vô nghiệm.
            
        3.  Bài toán nới lỏng cho ra nghiệm nguyên (cập nhật $LB$ nếu tốt hơn).
            

----------

# Logic Mệnh Đề (Propositional Logic)

### Các Quy Tắc Cơ Bản

#### 1. Phép Hội (Conjunction - $\land$)

-   Quy tắc Nhập (Introduction - $\land i$):
    
    $$\frac{\phi \quad \psi}{\phi \land \psi} \quad [\land i]$$
    
    Nếu bạn đã chứng minh được $\phi$ và bạn đã chứng minh được $\psi$, bạn có thể kết luận $\phi \land \psi$.
    
-   Quy tắc Loại bỏ (Elimination - $\land e$):
    
    $$\frac{\phi \land \psi}{\phi} \quad [\land e_1]$$
    
    $$\frac{\phi \land \psi}{\psi} \quad [\land e_2]$$
    
    Nếu bạn có $\phi \land \psi$, bạn có thể kết luận $\phi$. Bạn cũng có thể kết luận $\psi$.
    

#### 2. Phép Kéo theo (Implication - $\to$)

-   **Quy tắc Nhập (Introduction - $\to i$)**:
    
    ```
      ┌─────┐
      │  ϕ  │ assumption
      │  ⋮  │
      │  ψ  │
      └─────┘
    ───────── [→i]
       ϕ → ψ
    
    ```
    
    _Để chứng minh $\phi \to \psi$, hãy bắt đầu một "chứng minh con" (hộp) bằng cách giả sử $\phi$. Nếu bạn có thể suy ra $\psi$ bên trong hộp đó, bạn có thể kết luận $\phi \to \psi$ bên ngoài hộp._
    
-   Quy tắc Loại bỏ (Elimination - $\to e$ hay Modus Ponens - MP):
    
    $$\frac{\phi \quad \phi \to \psi}{\psi} \quad [\to e]$$
    
    Nếu bạn có $\phi$ và bạn có $\phi \to \psi$, bạn có thể kết luận $\psi$.
    

#### 3. Phép Tuyển (Disjunction - $\lor$)

-   Quy tắc Nhập (Introduction - $\lor i$):
    
    $$\frac{\phi}{\phi \lor \psi} \quad [\lor i_1]$$
    
    $$\frac{\psi}{\phi \lor \psi} \quad [\lor i_2]$$
    
    Nếu bạn có $\phi$, bạn có thể kết luận $\phi \lor \psi$. Nếu bạn có $\psi$, bạn cũng có thể kết luận $\phi \lor \psi$.
    
-   **Quy tắc Loại bỏ (Elimination - $\lor e$)**:
    
    ```
            ┌─────┐   ┌─────┐
            │  ϕ  │   │  ψ  │ assumption
            │  ⋮  │   │  ⋮  │
            │  χ  │   │  χ  │
            └─────┘   └─────┘
      ϕ ∨ ψ ───────────────── [∨e]
                   χ
    
    ```
    
    _Nếu bạn có $\phi \lor \psi$. Bạn cũng có hai "chứng minh con": một bắt đầu bằng giả sử $\phi$ và suy ra $\chi$, cái còn lại bắt đầu bằng giả sử $\psi$ và cũng suy ra $\chi$. Khi đó, bạn có thể kết luận $\chi$._
    

#### 4. Phép Phủ định (Negation - $\neg$)

-   **Quy tắc Nhập (Introduction - $\neg i$)**:
    
    ```
      ┌─────┐
      │  ϕ  │ assumption
      │  ⋮  │
      │  ⊥  │
      └─────┘
    ───────── [¬i]
        ¬ϕ
    
    ```
    
    _Để chứng minh $\neg \phi$, hãy bắt đầu một "chứng minh con" bằng cách giả sử $\phi$. Nếu bạn có thể suy ra mâu thuẫn ($\bot$) bên trong hộp đó, bạn có thể kết luận $\neg \phi$ bên ngoài hộp._
    
-   Quy tắc Loại bỏ (Elimination - $\neg e$):
    
    $$\frac{\phi \quad \neg \phi}{\bot} \quad [\neg e]$$
    
    Nếu bạn có cả $\phi$ và $\neg \phi$, bạn đã gặp mâu thuẫn ($\bot$).
    

#### 5. Mâu thuẫn (Contradiction - $\bot$)

-   Quy tắc Loại bỏ (Elimination - $\bot e$ hay Nguyên lý Bùng nổ):
    
    $$\frac{\bot}{\phi} \quad [\bot e]$$
    
    Từ một mâu thuẫn, bạn có thể suy ra bất kỳ mệnh đề $\phi$ nào.
    

#### 6. Phủ định Kép (Double Negation)

-   Quy tắc Nhập (Introduction - $\neg\neg i$, Derived):
    
    $$\frac{\phi}{\neg \neg \phi} \quad [\neg\neg i]$$
    
    Nếu có $\phi$, bạn có thể suy ra $\neg \neg \phi$.
    
-   Quy tắc Loại bỏ (Elimination - $\neg\neg e$, Classical - Không dùng trong Intuitionistic Logic):
    
    $$\frac{\neg \neg \phi}{\phi} \quad [\neg\neg e]$$
    
    Nếu có $\neg \neg \phi$, bạn có thể suy ra $\phi$.
    

----------

### Các Quy Tắc Suy Luận (Derived Rules)

-   Modus Tollens (MT):
    
    $$\frac{\phi \to \psi \quad \neg \psi}{\neg \phi} \quad [MT]$$
    
-   **Chứng minh bằng Phản chứng (Proof By Contradiction - PBC, _Classical_)**:
    
    ```
      ┌─────┐
      │ ¬ϕ  │ assumption
      │  ⋮  │
      │  ⊥  │
      └─────┘
    ───────── [PBC]
         ϕ
    
    ```
    
-   Luật Bài Trung (Law of Excluded Middle - LEM, Classical):
    
    $$\overline{\phi \lor \neg \phi} \quad [LEM]$$
    
    (Quy tắc này không có giả thiết, nó là một tiên đề có thể được chứng minh từ các quy tắc cơ bản khác (nếu dùng $\neg\neg e$ hoặc PBC)).
    

----------

# Logic Vị Từ (Predicate Logic)

### 1. Phép Bằng (Equality - $=$)

-   Quy tắc Nhập (Introduction - $=i$):
    
    $$\overline{t=t} \quad [=i]$$
    
    Mọi đối tượng (term) đều bằng chính nó.
    
-   Quy tắc Loại bỏ (Elimination - $=e$):
    
    $$\frac{t_1 = t_2 \quad \phi[x \Rightarrow t_1]}{\phi[x \Rightarrow t_2]} \quad [=e]$$
    
    Nếu $t_1$ bằng $t_2$, và ta có một công thức $\phi$ đúng khi thay $x$ bằng $t_1$, thì công thức đó cũng đúng khi thay $x$ bằng $t_2$. (Lưu ý: $\phi[x \Rightarrow t]$ là ký hiệu thay thế mọi vý hiện tự do của $x$ trong $\phi$ bằng $t$).
    

### 2. Lượng từ Phổ quát (Universal Quantifier - $\forall$)

-   **Quy tắc Nhập (Introduction - $\forall x \, i$)**:
    
    ```
      ┌──────┐
      │  x₀  │ fresh variable
      │  ⋮   │
      │ϕ[x⇒x₀]│
      └──────┘
    ────────── [∀x i]
       ∀x ϕ
    
    ```
    
    _Nếu bạn có thể chứng minh $\phi$ đúng cho một biến _hoàn toàn mới_ $x_0$ (không xuất hiện tự do ở bất kỳ giả thiết nào đang dùng), bạn có thể kết luận $\forall x \, \phi$._
    
-   Quy tắc Loại bỏ (Elimination - $\forall x \, e$):
    
    $$\frac{\forall x \, \phi}{\phi[x \Rightarrow t]} \quad [\forall x \, e]$$
    
    Nếu $\forall x \, \phi$ đúng, thì bạn có thể thay thế $x$ bằng bất kỳ đối tượng (term) $t$ nào (miễn là $t$ free for $x$ trong $\phi$ - để tránh "variable capture").
    

### 3. Lượng từ Tồn tại (Existential Quantifier - $\exists$)

-   Quy tắc Nhập (Introduction - $\exists x \, i$):
    
    $$\frac{\phi[x \Rightarrow t]}{\exists x \, \phi} \quad [\exists x \, i]$$
    
    Nếu bạn đã chứng minh được $\phi$ đúng cho một đối tượng cụ thể $t$ (khi thay $x$ bằng $t$), thì bạn có thể kết luận rằng tồn tại một $x$ làm cho $\phi$ đúng. (Yêu cầu $t$ phải free for $x$ trong $\phi$).
    
-   **Quy tắc Loại bỏ (Elimination - $\exists x \, e$)**:
    
    ```
                 ┌──────┐
                 │x₀ ϕ[x⇒x₀]│ assumption
                 │   ⋮    │
                 │   χ    │
                 └──────┘
      ∃x ϕ ───────────────── [∃x e]
                    χ
    
    ```
    
    _Nếu bạn có $\exists x \, \phi$. Bạn bắt đầu một "chứng minh con" bằng cách giả sử $\phi$ đúng cho một phần tử _hoàn toàn mới_ $x_0$ (tức là giả sử $\phi[x \Rightarrow x_0]$). Nếu bạn có thể suy ra một kết luận $\chi$ _không chứa $x_0$ tự do_ từ giả sử này, thì bạn có thể kết luận $\chi$ bên ngoài hộp. (Biến $x_0$ phải _fresh_, không xuất hiện tự do trong $\exists x \, \phi$, $\chi$, hay các giả thiết khác đang dùng ngoài giả thiết $\phi[x \Rightarrow x_0]$)._
    

----------
Điều kiện tối ưu:
- Một bài toán Lập trình tuyến tính (LPTT) có nghiệm tối ưu KHI VÀ CHỈ KHI miền khả thi (feasible set) không rỗng VÀ hàm mục tiêu (objective function) bị chặn (trên miền khả thi đó).

Miền khả thi & Nghiệm tối ưu:
- Miền khả thi bị chặn luôn có cả giá trị lớn nhất (max) và nhỏ nhất (min).
- Miền khả thi không bị chặn có thể có max hoặc min, nhưng không bao giờ có cả hai.

- Nếu tồn tại, nghiệm tối ưu (max/min) luôn luôn xảy ra tại ít nhất một đỉnh (extreme point / vertex) của miền khả thi.

  

Nghiệm cơ bản khả thi (Basic Feasible Solution - BFS):

  

- Là một nghiệm mà tại đó:

- Các biến không cơ bản (non-basic variables) có giá trị bằng 0.

- Các biến cơ bản (basic variables) có giá trị không âm (>= 0).

  

Phương pháp Đơn hình (Simplex Method):

  

- Chi phí rút gọn (Reduced Cost):

- Dùng để kiểm tra điều kiện tối ưu tại nghiệm cơ bản khả thi hiện tại.

- Chi phí rút gọn của các biến cơ bản (basic variables) luôn bằng 0.

Dưới đây là tóm tắt kiến thức Logic Hoare (bản không chứa trích nguồn) để bạn tiện sao chép vào "cheat sheet".

----------
# Hoare Triples

## 1. Khái niệm Cơ bản

### Bộ ba Hoare (Hoare Triple)

Một khẳng định về tính đúng đắn của chương trình, có dạng:

$(| \phi |) C (| \psi |)$

-   **$(| \phi |)$ (Tiền điều kiện - Precondition):** Khẳng định logic đúng _trước khi_ chạy chương trình $C$.
    
-   **$C$ (Command):** Đoạn chương trình (lệnh).
    
-   **$(| \psi |)$ (Hậu điều kiện - Postcondition):** Khẳng định logic đúng _sau khi_ $C$ chạy xong.
    

**Ý nghĩa:** Nếu $C$ bắt đầu trong trạng thái thỏa $\phi$, thì khi $C$ kết thúc, trạng thái sẽ thỏa $\psi$.

### Tính Đúng đắn Riêng phần (Partial Correctness)

-   **Ký hiệu:** $\models_{par} (|\phi|) C (|\psi|)$.
    
-   **Ý nghĩa:** Nếu $\phi$ đúng và $C$ được thực thi, _nếu $C$ dừng lại (terminates)_, thì $\psi$ sẽ đúng.
    
-   **Lưu ý:** _Không_ đảm bảo chương trình sẽ dừng. Một vòng lặp vô hạn luôn đúng "riêng phần" một cách tầm thường.
    

### Tính Đúng đắn Toàn phần (Total Correctness)

-   **Ký hiệu:** $\models_{tot} (|\phi|) C (|\psi|)$.
    
-   **Ý nghĩa:** Nếu $\phi$ đúng, $C$ được thực thi, thì $C$ _chắc chắn sẽ dừng_ và $\psi$ sẽ đúng.
    
-   **Công thức:** Tính đúng đắn Toàn phần = Tính đúng đắn Riêng phần + **Tính dừng (Termination)**.
    
----
#### Vậy tính đúng đắn toàn phần có thể suy ra được riêng phần nhưng không có ngược lại.
---

## 2. Quy tắc Chứng minh (Proof Calculus)

Đây là các quy tắc để suy luận tính đúng đắn $\vdash_{par} (|\phi|) C (|\psi|)$.

### Quy tắc 1: Phép gán (Assignment)

-   **Công thức:** $(| \psi[x \leftarrow E] |) \text{ } x := E \text{ } (| \psi |)$.
    
-   **Cách dùng (Suy luận ngược / $wp$):** Đây là Tiền điều kiện Yếu nhất ($wp$). Để $\psi$ đúng sau phép gán, ta chỉ cần thay thế mọi $x$ trong $\psi$ bằng $E$.
    
-   **Ví dụ:** $(| x + 1 > 5 |) \text{ } x := x + 1 \text{ } (| x > 5 |)$ (Vì $(x > 5)[x \leftarrow x+1] \equiv x+1 > 5$).
    

### Quy tắc 2: Tuần tự (Composition)

-   **Công thức:** $\frac{(|\phi|) C_1 (|\eta|) \quad , \quad (|\eta|) C_2 (|\psi|)}{(| \phi |) \text{ } C_1; C_2 \text{ } (| \psi |)}$
    
-   **Cách dùng:** Để chứng minh $C_1; C_2$, ta phải tìm một điều kiện $\eta$ (midcondition) làm hậu điều kiện cho $C_1$ và tiền điều kiện cho $C_2$.
    
-   **Thực hành (Proof Tableaux):** Ta thường làm ngược từ $\psi$, tính $\eta = wp(C_2, \psi)$, rồi tính $P = wp(C_1, \eta)$.
    
    ```
    (| P |)        <-- P = wp(C1, η)
      C1
    (| η |)        <-- η = wp(C2, ψ)
      C2
    (| ψ |)        <-- Hậu điều kiện
    
    ```
    

### Quy tắc 3: Rẽ nhánh (If-Statement)

-   Công thức (Chuẩn):
    
    $$\frac{(|\phi \land B|) \text{ } C_1 \text{ } (|\psi|) \quad , \quad (|\phi \land \neg B|) \text{ } C_2 \text{ } (|\psi|)}{(| \phi |) \text{ if } B \{ C_1 \} \text{ else } \{ C_2 \} \text{ } (| \psi |)}$$
    
-   Công thức (Dạng $wp$ / "Alternative"): (Cách này dùng để tìm $wp$)
    
    $$\frac{(|\phi_1|) \text{ } C_1 \text{ } (|\psi|) \quad , \quad (|\phi_2|) \text{ } C_2 \text{ } (|\psi|)}{(|(B \implies \phi_1) \land (\neg B \implies \phi_2)|) \text{ if } B \{ C_1 \} \text{ else } \{ C_2 \} \text{ } (| \psi |)}$$
    
-   **Cách dùng (dạng $wp$):** Tính $\phi_1 = wp(C_1, \psi)$ và $\phi_2 = wp(C_2, \psi)$. Tiền điều kiện yếu nhất cho cả lệnh `if` là $(B \implies \phi_1) \land (\neg B \implies \phi_2)$ hoặc $(B \land\phi_1) \lor (\neg B \land\phi_2)$.
    

### Quy tắc 4: Hệ quả (Implied / Rule of Consequence)

-   **Công thức:** $\frac{\vdash_{AR} \phi' \implies \phi \quad , \quad (|\phi|) C (|\psi|) \quad , \quad \vdash_{AR} \psi \implies \psi'}{(| \phi' |) \text{ } C \text{ } (| \psi' |)}$
    
-   **Cách dùng:** Cho phép ta:
    
    1.  **Tăng cường Tiền điều kiện (Strengthen Precondition):** Nếu $C$ đúng với $\phi$, nó cũng đúng với $\phi'$ mạnh hơn (vì $\phi' \implies \phi$).
        
    2.  **Nới lỏng Hậu điều kiện (Weaken Postcondition):** Nếu $C$ đạt được $\psi$, nó cũng đạt được $\psi'$ yếu hơn (vì $\psi \implies \psi'$).
        

----------

## 3. Quy tắc Vòng lặp `while`

### Vòng lặp - Riêng phần (Partial-While)

-   **Công thức:** $\frac{(|\psi \land B|) \text{ } C \text{ } (|\psi|)}{(| \psi |) \text{ while } B \{ C \} \text{ } (| \psi \land \neg B |)}$
    
-   **Bất biến Vòng lặp ($\psi$ - Loop Invariant):**
    
    -   $\psi$ là một khẳng định đúng _trước_ khi vào lặp.
        
    -   **Điều kiện chứng minh (Premise):** $(|\psi \land B|) \text{ } C \text{ } (|\psi|)$. Ta phải chứng minh rằng: nếu $\psi$ đúng _và_ vòng lặp chạy ( $B$ đúng), thì sau khi chạy thân $C$, $\psi$ _vẫn phải đúng_ (tính bảo toàn).
        
    -   **Kết luận:** Khi lặp dừng ($\neg B$ đúng), $\psi$ vẫn đúng.
        

### Vòng lặp - Toàn phần (Total-While)

-   **Công thức:** $\frac{(|\psi \land B \land 0 \le E = E_0|) \text{ } C \text{ } (|\psi \land 0 \le E < E_0|)}{(| \psi \land 0 \le E |) \text{ while } B \{ C \} \text{ } (| \psi \land \neg B |)}$
    
-   Quy tắc này thêm một **Biến thiên (Variant) $E$** để chứng minh tính dừng.
    
-   **Điều kiện của Biến thiên $E$:**
    
    1.  **$E \ge 0$:** $E$ luôn không âm (bị chặn dưới).
        
    2.  **$E$ giảm nghiêm ngặt:** Giá trị $E$ mới _phải nhỏ hơn_ giá trị $E$ cũ ( $E < E_0$) sau mỗi lần lặp.
        
    
    -   Ví dụ cho `while(z != x) {z=z+1; ...}` với $x \ge 0$: Bất biến $\psi$ là $(y=z!)$, Biến thiên $E$ là $(x-z)$.
