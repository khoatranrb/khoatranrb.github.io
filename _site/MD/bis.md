##### **1.1. Đường cong phù hợp**

* Chúng ta bắt đầu bằng một ví dụ hồi quy đơn giản. Giả sử ta quan sát các dữ liệu với đầu vào $x$ và đầu ra là $t$ ($x$, $t$ $\in R$).

  * Ví dụ dữ liệu được sinh ra từ hàm $\sin(2\pi x)$ ($x\in[0;1]$) với giá trị đích ($t$) bị ảnh hưởng bởi nhiễu Gauss.

* Cho tập huấn luyện quan sát được gồm $N$ mẫu $x$, với **x**$\equiv (x_1,...,x_N)^T$ cùng với các giá trị $t$, với **t**$\equiv (t_1,...,t_N)^T$. Ví dụ với $N=10$:

  <p>
      <img src='https://scontent.fsgn2-4.fna.fbcdn.net/v/t1.15752-9/91730107_240799220394942_3432198143934988288_n.png?_nc_cat=110&_nc_sid=b96e70&_nc_ohc=MjT6zMRgbKAAX88LIoJ&_nc_ht=scontent.fsgn2-4.fna&oh=61ee4631216bf1317e94351213ad55d7&oe=5EAE140A'>
      <center>H1.</center>
  </p>

* Mục đích của chúng ta là tạo một hàm dự đoán giá trị $\hat{t}$ từ một dữ liệu mới $\hat{x}$ bằng cách khai thác tập dữ liệu huấn luyện. Điều này nghĩa là ta phải khám phá ra hàm $\sin(2\pi x)$ từ một tập dữ liệu hữu hạn. Ở mặt tổng quát, mục tiêu của chúng ta là tìm một hàm số khái quát được dữ liệu thực từ dữ liệu huấn luyện. Đây là một nhiệm vụ thật sự khó. Hơn nữa, dữ liệu quan sát được đã bị ảnh hưởng bởi nhiễu.

* Trong hoàn cảnh này, chúng ta có thể xem xét hướng tới một đường cong phù hợp với dữ liệu có thể quan sát:
  $$
  y(x,w)=w_0+w_1x+w_2x^2+...+w_Mx^M=\sum_{j=0}^Mw_jx^j \tag1
  $$
  với $M$ là bậc của đường cong, **w**=$[w_0,...,w_M]$.

  Hàm số $y(x,w)$ phi tuyến với $x$ nhưng tuyến tính với **w**. Hàm số tuyến tính với các tham số chưa biết được gọi là **mô hình tuyến tính** *(linear model)*.

* Giá trị của các tham số **w** được xác định dựa trên tập dữ liệu huấn luyện (**x**,**t**) thông qua việc tối thiểu hàm lỗi - hàm đánh giá sai khác giữa nhãn $t$ và hàm dự đoán $f(x,w)$. Một hàm lỗi khá thông dụng là tổng bình phương lỗi của tất cả các điểm dữ liệu:
  $$
  E(w)=\frac{1}{2}\sum_{n=1}^N\{y(x_n,w)-t_n\}^2 \tag2
  $$

  <p>
      <img src='https://scontent.fsgn2-4.fna.fbcdn.net/v/t1.15752-9/91850803_1785567194954608_6833274740094795776_n.png?_nc_cat=106&_nc_sid=b96e70&_nc_ohc=O8IU64L7Uv8AX-EYzOw&_nc_ht=scontent.fsgn2-4.fna&oh=48f8fcb6a7aab8f57115c80902aec37e&oe=5EABD968'>
       <center>H2.</center>
</p>
  
  Giá trị nhỏ nhất của hàm lỗi là $0$ khi đường cong $y(x,w)$ đi qua tất cả điểm dữ liệu huấn luyện.
  
* Do $E(w)$ là hàm bậc $2$ của **w** nên tồn tại **w*** duy nhất sao cho hàm lỗi nhận giá trị nhỏ nhất. Khi đó đường cong sẽ là $y(x,w^*)$.

* Câu hỏi kế tiếp là: $M$ bằng bao nhiêu là hợp lý?.

  <p>
      <img src='https://scontent.fsgn2-2.fna.fbcdn.net/v/t1.15752-0/p280x280/91937881_2455568054753521_3073863022360395776_n.png?_nc_cat=103&_nc_sid=b96e70&_nc_ohc=hxHI3PLz294AX9617Jz&_nc_ht=scontent.fsgn2-2.fna&oh=aea72d66f5a4f6ae2ae4209c900ab051&oe=5EACD10B'>
       <center>H3.</center>
  </p>

  Việc chọn bậc $M$ của hàm số được gọi là *model comparison* hay *model selection*. Với $4$ ví dụ trên, ta có đưa ra vài nhận xét:

  * Hai đường cong với $M=0$ và $M=1$ đều không phù hợp với dữ liệu, không thể đại diện cho hàm $\sin(2\pi x)$ ($x\in[0;1]$).
  * Bằng trực giác, $M=3$ có vẻ là lựa chọn hợp lý nhất. 
  * Đường cong cuối cùng $M=9$ đi qua tất cả các điểm dữ liệu, $E(w^*)=0$. Hàm số này có giá trị hàm lỗi lý tưởng nhưng lại không thể đại diện cho hàm $\sin(2\pi x)$ ($x\in[0;1]$), không biểu diễn được đặc trưng của dữ liệu. Trường hợp này gọi là **overfitting**.

* Như đã đề cập ở trên, mục đích của chúng ta là tạo ra hàm dự đoán cho những dữ liệu không biết trước. Vì vậy, sau khi hàm $y(x,w^*)$ được học từ tập dữ liệu huấn luyện, chúng ta đánh giá hàm số này như sau:

  * Sinh ra $N$ dữ liệu từ hàm $\sin(2\pi x)$ ($x\in[0;1]$) với nhiễu Gauss (như đã đề cập ở đầu bài viết).

  * Sau đó dùng hàm lỗi để đánh giá. Đôi khi để thuận tiện, người ta có thể dùng hàm lỗi *Root mean square (RMS)*:
    $$
    E_{RMS}=\frac{2E(w^*)}{N} \tag3
    $$

    <p>
        <img src='https://scontent.fsgn2-4.fna.fbcdn.net/v/t1.15752-0/p280x280/91705864_152295676107431_1231464288808337408_n.png?_nc_cat=101&_nc_sid=b96e70&_nc_ohc=t7p_CxdAg3YAX8LtnI2&_nc_ht=scontent.fsgn2-4.fna&oh=0354ef8de0f009fb006d64a06fe6f943&oe=5EAD292A'>
         <center>H4.</center>
    </p>

* Tiếp theo, hãy xem xét bảng sau:

  <p>
      <img src='https://scontent.fsgn2-2.fna.fbcdn.net/v/t1.15752-0/p280x280/91928071_2624850214503101_2007620529086791680_n.png?_nc_cat=108&_nc_sid=b96e70&_nc_ohc=svI3CYkMz80AX9pl4-l&_nc_ht=scontent.fsgn2-2.fna&oh=b58f52a9365796565a94eee1b55bc6ae&oe=5EAC617E'>
       <center>H5.</center>
  </p>

  Thấy rằng, khi $M$ càng lớn thì giá trị của **w*** cũng lớn theo. Điều này nghĩa là, với tham số càng lớn thì hàm số càng dễ bắt được chính xác các điểm dữ liệu huấn luyện (như H3.). Mặt khác, tham số lớn khiến hàm số *quá linh hoạt*, *quá tập trung* vào dữ liệu, khiến cho nó quá nhạy cảm với nhiễu, dẫn đến việc dự đoán các dữ liệu ngoài tập huấn luyện không có kết quả tốt.

* Ví dụ tiếp, vẫn với $M=9$:

  <p>
      <img src='https://scontent.fsgn2-4.fna.fbcdn.net/v/t1.15752-0/p280x280/92312323_859889937836510_1267467320318492672_n.png?_nc_cat=111&_nc_sid=b96e70&_nc_ohc=YKCbg70_bQIAX93oqoJ&_nc_ht=scontent.fsgn2-4.fna&oh=f024ea3604542ba4e4f9eb567b80f2fa&oe=5EAF5543'>
      <center>H6. M=9</center>
  </p>

  Dễ thấy rằng, overfitting khó xảy ra khi tập dữ liệu huấn luyện lớn. Nói cách khác, khi dữ liệu lớn, ta có thể tìm ra hàm số phù hợp với dữ liệu dù $M$ có lớn.
  
* Một mô hình có quá linh hoạt *(nhiều tham số)* phải cần nhiều dữ liệu để tránh overfitting. Bây giờ cùng xem xét: Làm thế nào để tìm ra mô hình phù hợp khi lượng dữ liệu $N$ nhỏ cho hàm số phức tạp ($M$ lớn)? Trong trường hợp này, một kỹ thuật để tránh overfitting được gọi là **regularization**. Kỹ thuật này hạn chế các hệ số **w** quá lớn bằng cách cộng nó vào cùng với hàm lỗi $(2)$:
  $$
  \widetilde{E}(w)=\frac{1}{2}\sum_{n=1}^N\{y(x_n,w)-t_n\}^2+\frac{\lambda}{2}||w||^2=E(w)+\frac{\lambda}{2}||w||^2\tag4
  $$
  với $||w||^2\equiv w_1^2+w_2^2+...+w_M^2$ (lưu ý rằng công thức trên không có $w_0$), hệ số $\lambda$ ví như là "tầm quan trọng" giữa regularization và tổng bình phương lỗi. Nghĩa là, khi $\lambda$ càng lớn thì việc tối thiểu hóa $\widetilde{E}(w)$ sẽ tập trung vào việc tối thiểu $||w||^2$ nhiều hơn $E(w)$ và ngược lại.

* Khi tối thiểu $\widetilde{E}(w)$, ngoài việc tối thiểu sai số giữa dự đoán và thực tế, giá trị của **w** không được phép quá lớn khiến cho mô hình không quá tập trung vào dữ liệu. Đây là lý do không có $w_0$ trong $||w||^2$ do $w_0$ không tương tác với dữ liệu $x$ (xem công thức $(1)$). Kết quả của kỹ thuật regularization với $M=9$ và $N=10$:

  <p>
      <img src='https://raw.githubusercontent.com/khoatranrb/Img4Md/master/erm1.png'>
      <center>H7.</center>
  </p>

  <p>
      <img src='https://raw.githubusercontent.com/khoatranrb/Img4Md/master/erm.png'>
       <center>H8.</center>
  </p>

* Ảnh hưởng của $\lambda$ lên độ phức tạp của mô hình:

  <p>
      <img src='https://scontent-sin6-2.xx.fbcdn.net/v/t1.15752-0/p280x280/91978621_674577253291025_3402301490767855616_n.png?_nc_cat=109&_nc_sid=b96e70&_nc_ohc=d3a-39gZPsYAX8omJWI&_nc_ht=scontent-sin6-2.xx&oh=86457b65093291a2e358ee09b97c3574&oe=5EAD7E04'>
       <center>H9.</center>
  </p>

  Dựa vào H7. và H9., có thể thấy, $\lambda$ càng lớn khiến mô hình càng đơn giản. Ngược lại, $\lambda$ quá nhỏ khiến regularization gần như không có tác dụng.

* Như vậy là bài viết này đã cung cấp cho bạn đọc ý tưởng, các kỹ thuật tìm một hàm số phù hợp với dữ liệu cho trước.



##### **Tham khảo:**

* Mục 1.1 | Pattern Recognition and Machine Learning | C.M.Bishop