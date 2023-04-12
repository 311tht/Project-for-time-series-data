# Project-for-time-series-data
# Phần I: Mô tả project
Stock Price Prediction là một trong số những bài toán phổ biến trong chuỗi các bài toán liên quan đến dữ liệu Time Series. Ở đó, ta sẽ sử dụng các chỉ số ghi nhận được ở quá khứ của một cổ phiếu và dự đoán giá của nó ở tương lai, từ đó có thể đưa ra các quyết định đầu tư phù hợp.
Đối với các nhà đầu tư chứng khoán dựa vào phương pháp phân tích kỹ thuật (Technical Analysis), họ thường dựa vào giá đóng cửa điều chỉnh (Adjusted Closing Price) của cổ phiếu để thực hiện các quyết định mua/bán cổ phiếu. Vì vậy, trong project này, chúng ta sẽ xây dựng một mô hình dự đoán giá đóng cửa điều chỉnh của cổ phiếu công ty Tesla dựa vào các chỉ số được ghi nhận ở các ngày giao dịch chứng khoán trong khoảng thời gian từ ngày 06/29/2010 đến ngày 03/17/2017.
• Input: Các chỉ số của cổ phiếu trong 30 ngày giao dịch trước.
• Output: Giá đóng cửa điều chỉnh (Adjusted Closing Price) của ngày hiện tại.

# Phần II: Cài đặt chương trình
Trong phần này, chúng ta sẽ cài đặt và huấn luyện mô hình mạng nơ-ron dự đoán giá chứng khoán dựa trên các layer Bidirectional LSTM sử dụng Tensorflow.


Trong đó:
• Date: Ngày giao dịch.
• Open: Giá mở cửa.
• High: Giá cao nhất trong ngày.
• Low: Giá thấp nhất trong ngày.
• Close: Giá đóng cửa.
• Volume: Khối lượng giao dịch.
• Adj Close: Giá đóng cửa điều chỉnh.

# Phần III: Xây dựng mô hình
Các bạn sẽ xây dựng mô hình theo kiến trúc được mô tả như sau (danh sách dưới đây mô tả theo thứ tự trong tf.keras.Sequential):
• Input Layer: Nhận vào một vector các số nguyên (trong bài shape sẽ bằng = (30, 6)).
• Normalization Layer: Từ vector đầu vào, thực hiện chuẩn hóa dữ liệu sử dụng layer tf.keras.layers.Normalization (các bạn đọc thêm về layer này tại đây) được định nghĩa bên ngoài hàm như sau:
1 2
• BiLSTM Layer 1: Từ vector output của normalization layer, ta đưa vào layer BiLSTM đầu tiên với 128 units. Lưu ý rằng cần phải trả về vector output của toàn bộ timestep tại layer này để có thể làm input của layer BiLSTM tiếp theo.
• BiLSTM Layer 2: Layer BiLSTM thứ 2 với 64 units, trả về hidden state của toàn bộ timestep.
• BiLSTM Layer 3: Layer BiLSTM cuối cùng với 32 units, với layer này ta sẽ chỉ trả về vector output tại timestep cuối cùng.
• Fully-connected Layer: Từ vector output của BiLSTM layer cuối cùng, ta đưa vào một lớp fully-connected layer thứ nhất với 32 node với activation function là ’relu’.
• Output Layer: Fully-connected layer với 1 nodes (vì chỉ dự đoán giá của 1 ngày) và cài đặt activation = None.

Sau khi x 
• Output Layer: Fully-connected layer với 1 nodes (vì chỉ dự đoán giá của 1 ngày) và cài đặt activation = None.

Sau khi xây dựng mô hình với BiLSTM thì còn thêm một số mô hình như RNN, concat (RNN & LSTM) và XGBoost
