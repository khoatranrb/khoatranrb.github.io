##### **1. Lý thuyết quyết định Bayes**

* Đặt vấn đề: Một bài toán học có giám sát cho biết:

  * Không gian giả thuyết $H=\{h_1,h_2,...\}$
  * $P(h_i)$, $P(D|h_i)$ với $h_i \in H$, $D$ là dữ liệu quan sát được.

  Yêu cầu tìm $h\in H$ sao cho $P(h|D)$ lớn nhất.

* Quy tắc quyết định Bayes (*Maximum a posteriori*):

  * Ta có:
    $$
    P(h_i|D)=\frac{P(D|h_i)P(h_i)}{P(D)}
    $$
    với $P(D)=\sum_{i=1}^{|H|}P(D|h_i)P(h_i)$ là khả năng xuất hiện $D$. 

  * Do đó:
    $$
    \begin{align}
    h=h_{MAP}&=\arg\max\{P(h_i|D):h_i\in H\}\\
    &=\arg\max\{\frac{P(D|h_i)P(h_i)}{P(D)}:h_i\in H\}\\
    &=\arg\max\{P(D|h_i)P(h_i):h_i\in H\}
    \end{align}
    $$

* Quy tắc giả thuyết hợp lý nhất (*Maximum likelihood*):

  * Khi thiếu thông tin về các $P(h_i)$ trong $H$, ta giả thiết mọi giả thuyết trong $H$ có cùng xác suất, nghĩa là:
    $$
    P(h_i)=\frac{1}{|H|} \ \ \forall i
    $$

  * Khi đó, một giá trị $h\in H$ cho $P(D|h)$ cực đại cũng là giả thuyết $MAP$, ký hiệu là:
    $$
    h_{ML}=\arg\max\{P(D|h_i):h_i\in H\}
    $$



##### **2. Phân lớp Bayes**

* Xét bài toán gồm $k$ lớp $\{w_i\}_{i=1}^k$. Đã biết các $P(w_i)$, $P(x|w_i)$ và $x\in X$. Ta có:
  $$
  P(w_i|x)=\frac{P(x|w_i)P(w_i)}{P(x)}
  $$
  trong đó $P(x)=\sum_{i=1}^{k}P(x|w_i)P(w_i)$.

* Hàm quyết định cho mỗi lớp $w_i$ là $g(x,w_i)=P(w_i|x)$ hay $g(x,w_i)=P(x|w_i)P(w_i)$. Do đó ta có:
  $$
  w_{MAP}=\arg\max_{w} \{g(x,w)\}
  $$
  Nếu xác suất $P(w_i)$ như nhau thì:
  $$
  w_{ML}=\arg\max_{w}\{P(x|w)\}
  $$

* *Ví dụ:*

  * Một địa phương có $0.8\%$ dân số ung thư.
  * Xét nghiệm cho thấy $98\%$ người mắc bệnh ($B$) cho kết quả dương tính $(+)$, $97\%$ người không mắc bệnh ($KB$) cho kết quả âm tính $(-)$.
  * Một người xét nghiệm cho kết quả dương tính $(+)$ thì sẽ kết luận như nào?
  * *Lời giải:*
    * Dữ kiện từ đầu bài:
      * $P(B)=0.008$, $P(KB)=0.992$
      * $P(+|B)=0.98$, $P(-|B)=0.02$
      * $P(-|KB)=0.97$, $P(+|KB)=0.03$
    * Nên ta có:
      * $P(+|B)P(B)=0.98\times 0.008=0.00784$
      * $P(+|KB)P(KB)=0.03\times 0.992=0.02976$
    * Vì $P(+|KB)P(KB)>P(+|B)P(B)$ nên ta đưa ra kết luận *"không ung thư"*.

###### **2.1. Phân lớp cực tiểu rủi ro:**

* Giả sử sau khi phân lớp (giả sử $2$ lớp), ta quyết định hành động tương ứng. Hành động $a_1$ nếu phân lớp $w_1$ và $a_2$ nếu phân lớp $w_2$.

* Đặt $\lambda_{ij}=\lambda(a_i|w_j)$ là tổn thất phải chịu nếu trangj thái tự nhiên là $w_i$. Khi đó, tổn thất trung bình khi hành động tương ứng với mỗi quyết định phân lớp là:
  $$
  R(a_1|x)=\lambda_{11}P(w_1|x)+\lambda_{12}P(w_2|x)\\
  R(a_2|x)=\lambda_{21}P(w_1|x)+\lambda_{22}P(w_2|x)
  $$

* Trở lại ví dụ ở trên, trước tiên ta chuẩn hóa:
  $$
  P(B|+)=\frac{0.00784}{0.00784+0.02976}=0.21\\
  P(KB|+)=\frac{0.02976}{0.00784+0.02976}=0.79
  $$

  * Giả sử nếu quyết định ung thư ($B$) cho điều trị sớm ($S$) với chi phí $10$ triệu đồng, còn nếu không điều trị sớm ($M$) mà có bệnh, chi phí chữa trị sau đó là $100$ triệu đồng. Trong trường hợp này ta nên quyết định như nào?

    * Nếu điều trị sớm, dù có bệnh hay không thì vẫn tốn kém $10$ triệu:
      $$
      R(S|+)=10
      $$

    * Nếu không, với xác suất $21\%$ sau này sẽ phải điều trị, nên:
      $$
      R(M|+)=0.21\times 100=21
      $$

    * Như vậy, quyết định cực tiểu rủi ro là *"điều trị sớm"*.

* Khái quát lại, thiệt hại khi hành động $\alpha_i$ ứng với quyết định phân lớp tương ứng là:
  $$
  R(\alpha_i|x)=\sum_{j=1}^k\lambda(\alpha_i|w_j)P(w_j|x)
  $$

###### **2.2. Phân lớp Naive Bayes**

* Phân lớp Naive Bayes được áp dụng khi mẫu $x=[a_1,a_2,...,a_n]$ mô tả bởi liên kết các giá trị-thuộc tính. Khi đó:
  $$
  \begin{align}
  h_{MAP}&=\arg\max_{h\in H}\{P(h|a_1,a_2,...,a_n)\}\\
  &=\arg\max_{h\in H}\{\frac{P(a_1,a_2,...,a_n|h)P(h)}{P(a_1,a_2,...,a_n)}\}\\
  &=\arg\max_{h\in H}\{P(a_1,a_2,...,a_n|h)P(h)\}
  \end{align}
  $$
  Trong đó:
  $$
  P(a_1,a_2,...,a_n|h)=\prod_iP(a_i|h)
  $$
  Thay trở lại công thức trên, quy tắc phân lớp Naive Bayes sẽ quyết định:
  $$
  h_{NB}=\arg\max_{h\in H}\{P(h)\prod_iP(a_i|h)\}
  $$

###### **2.3. Phân lớp Bayes khi mỗi lớp có phân bố chuẩn**

* Xét lớp $w_i$ có phân bố chuẩn, hàm mật độ dạng:
  $$
  P(x|w_i)=\frac{1}{(2\pi)^{n/2}|\Sigma_i|^{1/2}}\exp(-\frac{1}{2}(x-\mu_i)^T\Sigma_i^{-1}(x-\mu_i))
  $$
  trong đó:

  * $n$ là số chiều của $x$
  * $\mu_i$ là vector trung bình của lớp $w_i$
  * $\Sigma_i$ là ma trận hiệp phương sai của lớp $w_i$

* Hàm quyết định cho lớp $w_i$:
  $$
  \begin{align}
  g_i(x)&=P(w_i)P(x|w_i)\\
  &=P(w_i)\frac{1}{(2\pi)^{n/2}|\Sigma_i|^{1/2}}\exp(-\frac{1}{2}(x-\mu_i)^T\Sigma_i^{-1}(x-\mu_i))
  \end{align}
  $$
  Lấy logarit hai vế:
  $$
  d_i(x)=\ln(g(x))=\ln P(w_i)-\frac{n}{2}\ln 2\pi-\frac{1}{2}\ln |\Sigma_i|-\frac{1}{2}(x-\mu_i)^T\Sigma_i^{-1}(x-\mu_i)
  $$
  Loại bỏ các hằng số, ta được hàm quyết định cuối cùng:
  $$
  d_i(x)=\ln P(w_i)-\frac{1}{2}\ln |\Sigma_i|-\frac{1}{2}(x-\mu_i)^T\Sigma_i^{-1}(x-\mu_i)
  $$

