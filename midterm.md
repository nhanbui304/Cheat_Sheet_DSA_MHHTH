

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


## Models trong Logic Vị từ

**Mục đích:** Model (Mô hình) cung cấp **ngữ nghĩa** (meaning) cụ thể cho các ký hiệu trong một ngôn ngữ logic vị từ. Nó định nghĩa "thế giới" mà các công thức logic sẽ được diễn giải là đúng hay sai.

**Thành phần của Model $\mathcal{M}$:** Cho một tập ký hiệu hàm $\mathcal{F}$ và tập ký hiệu vị từ $\mathcal{P}$, một model $\mathcal{M}$ cho $(\mathcal{F}, \mathcal{P})$ bao gồm:

1.  **Universe (Không gian mẫu) $A$:** Một tập hợp **không rỗng** chứa các đối tượng mà logic đang nói đến (ví dụ: tập số tự nhiên $\mathbb{N}$, tập các chuỗi nhị phân, tập hợp người,...).
2.  **Interpretation (Diễn giải) cho Ký hiệu hàm $f \in \mathcal{F}$:**
    * **Hằng số (Arity 0):** Mỗi ký hiệu hằng $c \in \mathcal{F}$ được gán một **phần tử cụ thể** $c^{\mathcal{M}} \in A$.
    * **Hàm (Arity $n > 0$):** Mỗi ký hiệu hàm $f \in \mathcal{F}$ với arity $n$ được gán một **hàm cụ thể** $f^{\mathcal{M}}: A^n \to A$.
3.  **Interpretation cho Ký hiệu vị từ $P \in \mathcal{P}$:**
    * Mỗi ký hiệu vị từ $P \in \mathcal{P}$ với arity $n > 0$ được gán một **quan hệ (tập con)** $P^{\mathcal{M}} \subseteq A^n$. $P^{\mathcal{M}}$ chứa các bộ $(a_1, ..., a_n)$ các phần tử từ $A$ mà làm cho vị từ $P$ đúng.

**Ví dụ:**

* Ngôn ngữ: $\mathcal{F} = \{0, succ\}$, $\mathcal{P} = \{Even\}$ (0 là hằng, succ là hàm 1 ngôi, Even là vị từ 1 ngôi).
* Model $\mathcal{M}$:
    * Universe $A = \mathbb{N} = \{0, 1, 2, ...\}$.
    * $0^{\mathcal{M}} = 0$ (số không).
    * $succ^{\mathcal{M}}(n) = n + 1$ (hàm cộng thêm 1).
    * $Even^{\mathcal{M}} = \{n \in \mathbb{N} \mid n \text{ là số chẵn}\} = \{0, 2, 4, ...\}$.

**Environment (Môi trường) $l$:**

* Để xử lý các **biến tự do** (free variables) trong công thức, ta cần một môi trường $l$.
* $l$ là một hàm ánh xạ từ tập các biến (var) vào universe $A$ ($l: \text{var} \to A$). Nó gán giá trị cụ thể trong $A$ cho mỗi biến.
* Ký hiệu $l[x \mapsto a]$: Môi trường giống $l$ ngoại trừ việc biến $x$ được gán giá trị $a$.

**Satisfaction Relation (Quan hệ thỏa mãn) $\mathcal{M} \models_l \phi$:**

Đọc là: "Model $\mathcal{M}$ **thỏa mãn** công thức $\phi$ dưới môi trường $l$". Nó định nghĩa khi nào một công thức là đúng trong model:

* **Vị từ:** $\mathcal{M} \models_l P(t_1, ..., t_n)$ nếu bộ giá trị $(a_1, ..., a_n)$ (kết quả của việc tính các term $t_1, ..., t_n$ trong $\mathcal{M}$ dưới $l$) thuộc về $P^{\mathcal{M}}$.
* **Phủ định:** $\mathcal{M} \models_l \neg \psi$ nếu $\mathcal{M} \models_l \psi$ không đúng.
* **Hội:** $\mathcal{M} \models_l \psi_1 \land \psi_2$ nếu cả $\mathcal{M} \models_l \psi_1$ và $\mathcal{M} \models_l \psi_2$ đều đúng.
* **Tuyển:** $\mathcal{M} \models_l \psi_1 \lor \psi_2$ nếu ít nhất một trong $\mathcal{M} \models_l \psi_1$ hoặc $\mathcal{M} \models_l \psi_2$ đúng.
* **Kéo theo:** $\mathcal{M} \models_l \psi_1 \to \psi_2$ nếu $\mathcal{M} \models_l \psi_1$ sai hoặc $\mathcal{M} \models_l \psi_2$ đúng.
* **Với mọi ($\forall$):** $\mathcal{M} \models_l \forall x \psi$ nếu $\mathcal{M} \models_{l[x \mapsto a]} \psi$ đúng **với mọi** phần tử $a \in A$.
* **Tồn tại ($\exists$):** $\mathcal{M} \models_l \exists x \psi$ nếu $\mathcal{M} \models_{l[x \mapsto a]} \psi$ đúng với **ít nhất một** phần tử $a \in A$.

**Sentence (Câu đóng):**

* Nếu công thức $\phi$ **không có biến tự do**, nó được gọi là một câu đóng (sentence).
* Đối với câu đóng, việc $\mathcal{M} \models_l \phi$ đúng hay sai **không phụ thuộc** vào môi trường $l$.
* Ta có thể viết gọn là $\mathcal{M} \models \phi$ (model $\mathcal{M}$ thỏa mãn câu $\phi$).
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
---
## 1. Lý thuyết Quy hoạch tuyến tính (LP)

-   **Định nghĩa:** Tối ưu (tối đa hóa hoặc tối thiểu hóa) một hàm mục tiêu **tuyến tính** dưới các ràng buộc **tuyến tính** (bất đẳng thức hoặc đẳng thức). Các biến quyết định thường là **liên tục** và không âm ($x \ge 0$).
    
-   **Các dạng:**
    
    -   Dạng chuẩn (Standard Form): Thường dùng cho phương pháp Simplex.
        
        $min \ c^T x$
        
        s.t. $Ax = b$
        
        $x \ge 0$
        
        (Lưu ý: Bất đẳng thức được chuyển thành đẳng thức bằng cách thêm/bớt biến bù - slack/surplus variables).
        
    -   **Dạng chính tắc (Canonical Form):** Thường là $min \ c^T x$ s.t. $Ax \le b, x \ge 0$ hoặc $max \ c^T x$ s.t. $Ax \le b, x \ge 0$.
        
    -   **Dạng tổng quát:** Kết hợp các ràng buộc $=, \le, \ge$.
        
-   **Tính chất hình học:**
    
    -   Miền khả thi (Feasible Region) là một tập lồi đa diện (convex polyhedron).
        
    -   Nếu tồn tại nghiệm tối ưu và miền khả thi có điểm cực biên (extreme point/vertex), thì ít nhất một nghiệm tối ưu nằm tại một điểm cực biên.
        
    -   Điểm cực biên (extreme point/vertex/corner point) tương đương với Nghiệm cơ bản khả thi (Basic Feasible Solution - BFS).
        
-   **Điều kiện tồn tại nghiệm tối ưu:**
    
    -   Một bài toán LPTT có nghiệm tối ưu KHI VÀ CHỈ KHI miền khả thi không rỗng VÀ hàm mục tiêu bị chặn trên miền khả thi đó.
        
-   **Miền khả thi & Nghiệm tối ưu:**
    
    -   Miền khả thi bị chặn luôn có cả giá trị lớn nhất (max) và nhỏ nhất (min).
        
    -   Miền khả thi không bị chặn có thể có max hoặc min, nhưng không bao giờ có cả hai.
        
    -   Nếu tồn tại, nghiệm tối ưu (max/min) luôn luôn xảy ra tại ít nhất một đỉnh (extreme point / vertex) của miền khả thi. (Câu 14 - ý I)
        
    -   Nghiệm tối ưu **không bao giờ** nằm _bên trong_ miền khả thi. (Câu 14 - ý III)
        
    -   Có thể nằm trên _cạnh_ (không phải đỉnh) nếu có vô số nghiệm tối ưu.
        
-   **Phép biến đổi:** $\min(Z)$ tương đương với $\max(-Z)$. (Câu 31)
    

----------

## 2. Phương pháp Đơn hình (Simplex Method) - Dùng cho LP

-   **Ý tưởng:** Di chuyển giữa các BFS kề nhau trên biên của miền khả thi, mỗi bước cải thiện giá trị hàm mục tiêu, cho đến khi đạt tối ưu.
    
-   **Biến cơ sở (Basic Variable):**
    
    -   Chi phí rút gọn (Reduced Cost) **luôn bằng 0**. (Câu 13)
        
    -   Trong bảng đơn hình, giá trị của chúng được đọc ở cột RHS (vế phải).
        
-   **Biến phi cơ sở (Non-basic Variable):**
    
    -   Giá trị (Value) của chúng **luôn bằng 0**. (Câu 20)
        
    -   Chi phí rút gọn của chúng (hàng $Z_j - C_j$ hoặc $r_N$) cho biết tính tối ưu.
        
-   **Nghiệm cơ bản (Basic Solution):**
    
    -   Tìm bằng cách cho $n-m$ biến (phi cơ sở) bằng 0 và giải hệ $m$ phương trình cho $m$ biến còn lại ($x_N=0 \implies x_B = B^{-1}b$). (Câu 32)
        
    -   Nghiệm cơ bản có thể **không khả thi** (not feasible) nếu có giá trị âm ($x_B = B^{-1}b \not\ge 0$). (Câu 20)
        
-   **Nghiệm cơ bản khả thi (BFS):**
    
    -   Là một nghiệm cơ bản mà tất cả các biến $\ge 0$ ($x_B = B^{-1}b \ge 0$). (Câu 33)
        
    -   Thuật toán Đơn hình di chuyển giữa các BFS kề nhau.
        
-   **Bảng đơn hình (Tableau):**
    
    -   Đưa LP về dạng chuẩn ($Ax=b, x \ge 0$). Lập bảng ban đầu.
        
    -   Dòng cuối cùng chứa hệ số của hàm mục tiêu (viết lại dạng $Z - c^T x = 0$).
        
-   **Điều kiện tối ưu (Dừng thuật toán):** (Câu 35)
    
    1.  **Khả thi:** Cột vế phải (RHS) $\ge 0$. (Câu 34)
        
    2.  **Tối ưu:** Hàng chi phí rút gọn ($r_N$ hoặc $\Delta$) thỏa mãn:
        
        -   **Bài toán MIN:** Tất cả chi phí rút gọn $\ge 0$.
            
        -   **Bài toán MAX:** Tất cả chi phí rút gọn $\le 0$.
            
-   **Các bước lặp (Bài toán MIN):**
    
    1.  **Chọn biến vào (Entering Variable):** Chọn cột có chi phí rút gọn _âm nhất_ trong dòng cuối cùng. Cột tương ứng là _cột xoay_.
        
    2.  **Chọn biến ra (Leaving Variable):** Tính tỷ số $\lambda$ = (Cột RHS) / (Phần tử dương trong cột xoay). Chọn dòng có tỷ số $\lambda$ _không âm nhỏ nhất_. Dòng tương ứng là _dòng xoay_. Phần tử xoay là giao của dòng và cột xoay.
        
    3.  **Phép xoay (Pivoting):** Biến đổi dòng để phần tử xoay thành 1, các phần tử khác trong cột xoay thành 0. Cập nhật bảng. Lặp lại từ Bước 1.
        
-   **Dấu hiệu nghiệm không bị chặn (Unbounded):** (Câu 19)
    
    -   Khi đã chọn cột xoay (biến vào), nhưng **tất cả hệ số trong cột đó đều $\le 0$**.
        
    -   Không thể thực hiện phép thử tỉ lệ (ratio test) để chọn dòng xoay.
        
-   **Kiểm tra một điểm có phải BFS tối ưu không (Bài MIN):** (Câu 18)
    
    1.  **Kiểm tra Khả thi:** Thay điểm vào _tất cả_ ràng buộc (kể cả $x_i \ge 0$). Phải thỏa mãn hết.
        
    2.  **Kiểm tra Cơ sở:** Các biến $> 0$ là biến cơ sở, biến $= 0$ là phi cơ sở. Ma trận cột $A$ ứng với các biến cơ sở ($B$) phải khả nghịch ($\det(B) \ne 0$).
        
    3.  **Kiểm tra Tối ưu:** Tính chi phí rút gọn $r_j = c_j - c_B^T B^{-1} A_j$ cho _tất cả các biến phi cơ sở $x_j$_. Nếu tất cả $r_j \ge 0$ thì là tối ưu.
        

----------

## 3. Quy hoạch nguyên (Integer Linear Programming - ILP)

-   **Định nghĩa:** Bài toán LP trong đó một phần hoặc tất cả các biến quyết định phải nhận giá trị **nguyên**.
    
-   **Các loại:**
    
    -   **ILP thuần túy (Pure ILP):** Tất cả các biến là số nguyên ($x \in \mathbb{Z}^n$).
        
    -   **ILP hỗn hợp (Mixed ILP - MILP):** Một số biến nguyên, một số biến liên tục.
        
    -   **ILP nhị phân (Binary ILP - BIP):** Tất cả các biến chỉ nhận giá trị 0 hoặc 1 ($x \in \{0, 1\}^n$).
        
-   **Nới lỏng LP (LP Relaxation):** Bỏ qua ràng buộc nguyên của các biến (ví dụ: $x_i \in \{0, 1\}$ trở thành $0 \le x_i \le 1$).
    
-   **Tính chất:** Giá trị tối ưu của LP relaxation là một **chặn** (cận trên $UB$ cho bài toán max, cận dưới $LB$ cho bài toán min) cho giá trị tối ưu của ILP ($Z_{LP} \ge Z_{IP}$ cho bài toán max). Nếu nghiệm tối ưu của LP relaxation là nguyên, nó cũng là nghiệm tối ưu cho ILP.
    

----------

## 4. Nhánh và Cận (Branch and Bound - B&B) - Dùng cho ILP

-   **Mục đích:** Giải bài toán Quy hoạch _nguyên_ (ILP).
    
-   **Ý tưởng:** Chia bài toán ILP thành các bài toán con nhỏ hơn (**nhánh** - branch), và sử dụng nghiệm của LP relaxation để loại bỏ các nhánh không chứa nghiệm tối ưu (**cận** - bound).
    
-   **Bước đầu tiên (Nút gốc - Root Node):** (Câu 2, 30)
    
    -   Giải **nới lỏng tuyến tính (LP Relaxation)** của bài toán gốc.
        
    -   Giá trị tối ưu $Z_{LP}$ là cận đầu tiên (UB cho max, LB cho min).
        
-   **Các cận (cho bài toán MAX):**
    
    -   **Cận trên (Upper Bound - UB):** Giá trị $Z_{LP}$ của nghiệm nới lỏng LP tại một nút (luôn $\ge$ nghiệm nguyên tốt nhất trong nhánh đó).
        
    -   **Cận dưới (Lower Bound - LB):** Giá trị $Z^*$ của nghiệm _nguyên_ khả thi tốt nhất tìm được cho đến nay (incumbent). Khởi tạo $Z^* = -\infty$ cho bài toán max.
        
-   **Quy tắc cắt tỉa / Loại bỏ nút (Fathoming/Pruning):** (Câu 28) Dừng xét một nhánh (nút) khi:
    
    1.  **Bởi Cận:** Cận của nút không tốt hơn incumbent ($UB \le LB$ cho bài toán MAX). Nhánh này không có khả năng cho nghiệm tốt hơn nghiệm nguyên đã tìm thấy.
        
    2.  **Bởi Tính không khả thi:** Bài toán nới lỏng LP tại nút đó vô nghiệm.
        
    3.  **Bởi Nghiệm nguyên:** Bài toán nới lỏng LP cho ra nghiệm nguyên. Nếu tốt hơn incumbent, cập nhật incumbent ($LB$ hoặc $Z^*$).
        
-   **Phân nhánh (Branching):**
    
    -   Nếu một nút không bị loại bỏ và nghiệm LP relaxation $x_{LP}$ của nó không nguyên.
        
    -   Chọn một biến $x_k$ có giá trị không nguyên $v_k$ (ví dụ: biến "phân số nhất").
        
    -   Tạo ra hai bài toán con mới bằng cách thêm ràng buộc: $x_k \le \lfloor v_k \rfloor$ và $x_k \ge \lceil v_k \rceil$ (hoặc $x_k=0$ và $x_k=1$ cho BIP).
        
-   **Kết thúc:** Khi không còn nút nào đang hoạt động (chưa bị loại bỏ). Incumbent cuối cùng là nghiệm tối ưu.
    

----------

## 5. Một số mô hình ILP/BIP phổ biến

-   **Bài toán Cái túi (Knapsack Problem - 0-1):** Chọn các vật phẩm (giá trị $v_j$, trọng lượng $w_j$) để tối đa tổng giá trị $\sum v_j x_j$ mà tổng trọng lượng $\sum w_j x_j \le b$, với $x_j \in \{0, 1\}$. Ứng dụng trong Lập ngân sách vốn (Capital Budgeting).
    
-   **Bài toán Phủ tập hợp (Set Covering):** Chọn ít nhất một phương án để "phủ" các yêu cầu với chi phí tối thiểu $\sum_{j} c_j x_j$ s.t. $\sum_{j \in S_i} x_j \ge 1$ cho mỗi yêu cầu $i$, $x_j \in \{0, 1\}$. (Ví dụ: đồn cảnh sát).
    
-   **Bài toán Định vị cơ sở (Facility Location):** Quyết định mở cơ sở ở đâu ($x_j \in \{0, 1\}$) và phân bổ khách hàng $i$ đến cơ sở $j$ ($y_{ij}$) thế nào để tối thiểu chi phí.
    
-   **Bài toán Vận tải (Transportation):** Tối thiểu chi phí vận chuyển hàng từ nguồn $i$ (cung $r_i$) đến đích $j$ (cầu $d_j$). Biến $x_{ij}$ là lượng vận chuyển. Ràng buộc cung $\sum_j x_{ij} \le r_i$ và cầu $\sum_i x_{ij} \ge d_j$. Có thể là LP hoặc ILP. Bài toán cân bằng nếu $\sum r_i = \sum d_j$.
    
-   **Kỹ thuật mô hình hóa nhị phân:**
    
    -   Ràng buộc phủ ($\sum x_i \ge 1$), đóng gói ($\sum x_i \le 1$), phân hoạch ($\sum x_i = 1$).
        
    -   Ràng buộc phụ thuộc ($x_i \le x_j$ - nếu chọn i thì phải chọn j).
        
    -   Ràng buộc "hoặc/hoặc", "nếu-thì".

----------
# Bài toán tính số nghiệm
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

