##### **2.3. Tối thiểu rủi ro thực nghiệm với xu hướng quy nạp**

* Ở bài viết trước, chúng ta đã chứng minh phương pháp *ERM* có thể dẫn đến *overfitting*. Bây giờ chúng ta sẽ tìm cách cải thiện nó bằng việc tìm các điều kiện để đảm bảo *ERM* không bị *overfit*.

* Một trong những phương pháp chung khi thực hiện *ERM* là giới hạn không gian tìm kiếm. Cụ thể, bộ học sẽ chọn trước một tập các hàm dự đoán (trước khi nhìn thấy dữ liệu). Tập các hàm dự đoán này gọi là "không gian giả thuyết" (*hypothesis class*), ký hiệu là $H$. Mỗi hàm $h\in H$ ánh xạ $X\to Y$. Cho trước $S$ và $H$, bộ học $ERM_H$ sử dụng *ERM* chọn ra hàm dự đoán $h\in H$ sao cho lỗi trên $S$ nhỏ nhất:
  $$
  ERM_H(S)\in \arg \min_{h\in H}L_S(h)
  $$

* Lựa chọn không gian hạn chế lý tưởng khi có hiểu biết trước về vấn đề cần học. Ví dụ, về vấn đề dự đoán trái đu đủ chín hay chưa (đã đề cập ở bài viết trước), chúng ta có thể chọn giả thuyết $H$ là tập các hình chữ nhật (với các cạnh song song với $2$ trục). Ở phần dưới, chúng ta sẽ chứng minh $ERM_H$ cho không gian giả thuyết này không bị *overfit*.

* Câu hỏi đặt ra bây giờ là: Không gian giả thuyết như nào thì giúp $ERM_H$ tránh được *overfitting*? Hãy cùng nhau khám phá ở phần còn lại của bài viết.

###### **2.3.1. Không gian giả thuyết**

* Cách thức đơn giản nhất để giới hạn không gian tìm kiếm là đặt giới hạn trên cho kích cỡ của $H$ (số lượng $h\in H$). Chúng ta cần chứng minh với $H$ hữu hạn, $ERM_H$ sẽ không bị *overfit*, nếu dữ liệu huấn luyện đủ lớn (size của $S$ phụ thuộc vào size của $H$).

* Với giả thiết $H$ hữu hạn: cho tập huấn luyện $S$, hàm gán nhãn $f:X\to Y$, ký hiệu $h_S$ là kết quả khi áp dụng $ERM_H$ lên $S$:
  $$
  h_S\in \arg \min_{h\in H}L_S(h)
  $$

* **Định nghĩa** (Giả thuyết tính khả thi):

  Tồn tại $h^*\in H$ sao cho $L_{(D,f)}(h^*)=0$. Nghĩa là $h^*$ dự đoán chính xác tất cả các mẫu trên $D$, do đó $L_S(h^*)=0$ nếu $S$ lấy mẫu từ $D$.

  Ý nói rằng, mọi giả thuyết từ $ERM$ đều có thể cho kết quả $L_S(h_S)=0$. Tuy nhiên, cái ta quan tâm là lỗi trên $D$ chứ không phải trên $S$.

* $L_S$ có thể đại diện cho $L_D$ nếu $m$ điểm thuộc $S$ được lấy mẫu trên $D$ một cách độc lập. Ký hiệu $S\sim D^m$. Tập $S$ được coi là cửa sổ để bộ học hình dung ra $D$ và $f$. $S$ có thể có hoặc không đại diện cho $D$. Tập $S$ càng lớn thì càng có nhiều khả năng đại diện cho $D$.

* Giả sử với xác suất $\delta$ tập $S$ không đại diện cho $D$, ta có $1-\delta$ là sự tự tin đối với hàm dự đoán $h_S$. Ta ký hiệu $\epsilon$ tượng trưng cho xác suất dự đoán sai của mô hình. Nếu $L_{(D,f)}>\epsilon$ nghĩa là việc học thất bại, ngược lại, nếu $L_{(D,f)}\le\epsilon$ chứng tỏ việc học thành công.

* **Ta cần tìm xác suất cận trên của việc lấy mẫu $m$ dữ liệu dẫn đến việc học thất bại.** Giả sử $S|_x=(x_1,...,x_m)$ là tập huấn luyện. Ta cần tìm:
  $$
  D^m(\{S|_x:L_{(D,f)}(h_S)>\epsilon\})
  $$

  * Gọi $H_B$ là tập giả thiết cho kết quả kém:
    $$
    H_B=\{h\in H:L_{(D,f)}(h)>\epsilon\}
    $$

  * Gọi
    $$
    M=\{S|_x:\exist h\in H_B,L_S(h)=0\}
    $$
    hay
    $$
    M=\cup_{h\in H_B}\{S|_x:L_S(h)=0\}
    $$
    là tập các bộ huấn luyện lừa được thuật toán học. Nghĩa là $h\in H_B$, $L_{(D,f)}(h_S))>\epsilon$ nhưng lại cho kết quả tốt trên $S|_x$. Ta có:
    $$
    \{S|_x:L_{(D,f)}(h_S)>\epsilon\}\subseteq M
    $$

  * Do đó ta có:
    $$
    D^m(\{S|_x:L_{(D,f)}(h_S)>\epsilon\})\le D^m(M)=D^m(\{S|_x:\exist h\in H_B,L_S(h)=0\})\tag1
    $$

* **Bổ đề** (Union Bound): Cho hai tập $A$, $B$ và phân phối $D$:
  $$
  D(A\cup B)\le D(A)+D(B) \tag2
  $$

  * Áp dụng $(2)$ vào $(1)$ ta được:
    $$
    D^m(\{S|_x:L_{(D,f)}(h_S)>\epsilon\})\le\sum_{h\in H_B}D^m(\{S|_x:L_S(h)=0\}) \tag3
    $$

* Vì $S$ lấy mẫu từ $D$ nên ta có:
  $$
  \begin{align}
  D^m(\{S|_x:L_S(h)=0\})&=D^m(\{S|_x:\forall i,h(x_i)=f(x_i)\})\\
  &=\prod_{i=1}^mD(\{x_i:h(x_i)=f(x_i)\})
  \end{align} \tag4
  $$

  * Như giả thuyết ban đầu ta có:
    $$
    D(\{x_i:h(x_i)=f(x_i)\})=1-L_{(D,f)}(h)\le1-\epsilon
    $$

  * Do đó:
    $$
    D^m(\{S|_x:L_S(h)=0\})\le(1-\epsilon)^m\le e^{-\epsilon m} \tag5
    $$

    * Chứng minh:

      Có $\epsilon\in[0,1]$, $m>0$,  cần chứng minh: $(1-\epsilon)^m\le e^{-\epsilon m}$.
      $$
      \begin{align}
      &(1-\epsilon)^m\le e^{-\epsilon m}\\
      &\to \ln[(1-\epsilon)^m]\le \ln[e^{-\epsilon m}]\\
      &\to m\ln(1-\epsilon)\le-\epsilon m\\
      &\to \ln(1-\epsilon)\le-\epsilon\\
      &\to \epsilon+\ln(1-\epsilon)\le0
      \end{align}
      $$
      Với $g(\epsilon)=\epsilon+\ln(1-\epsilon)$, ta có:
      $$
      \frac{\partial g}{\partial\epsilon}=1-\frac{1}{1-\epsilon}\le0 \ \forall\epsilon\in[0,1]
      $$
      Do đó:
      $$
      \max_{\epsilon\in[0,1]}g(\epsilon)=g(0)=0
      $$
      Vậy ta đã chứng minh được bất đẳng thức trên.

* Từ $(3)(4)(5)$ ta có:
  $$
  D^m(\{S|_x:L_{(D,f)}(h_S)>\epsilon\})\le|H_B|e^{-\epsilon m}\le|H|e^{-\epsilon m}
  $$

* **Hệ quả:** Cho $H$ là tập giả thuyết hữu hạn, $\delta\in(0,1)$, $\epsilon>0$ và $m$ thỏa mãn
  $$
  m\ge\frac{\log(\frac{|H|}{\delta})}{\epsilon}
  $$
  thì với độ tự tin ít nhất $1-\delta$ thuật toán $ERM_H$ cho hàm dự đoán $h_S$ tốt, nghĩa là $L_{(D,f)}(h_S)<\epsilon$.



##### **Tham khảo:**

* [1] <a href='https://www.cs.huji.ac.il/~shais/UnderstandingMachineLearning/understanding-machine-learning-theory-algorithms.pdf'>Chương 2.3 | Understanding Machine Learning from theory to algorithms.</a>
* [2] <a href='https://uetailab.com/index.php/2019/10/18/uml2-3-cuc-tieu-hoa-sai-so-thuc-nghiem-tren-khong-gian-gia-thiet-rut-gon-thien-kien-qui-nap-inductive-bias/'>UML2.3 – Cực tiểu hóa sai số thực nghiệm trên không gian giả thiết rút gọn | UET_AI_Lab.</a>