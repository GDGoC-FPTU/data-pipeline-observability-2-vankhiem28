# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** AI20K-XXXX
**Name:** Van khiem
**Date:** 2026-06-10

---

## 1. Kết quả thí nghiệm

Chạy `agent_simulation.py` với 2 bộ dữ liệu và ghi lại kết quả:

| Scenario | Agent Response | Accuracy (1-10) | Notes |
|----------|----------------|-----------------|-------|
| Clean Data (`processed_data.csv`) | Agent: Based on my data, the best choice is Laptop at $1200. | 9 | Dữ liệu sạch, category đã được chuẩn hóa và giá trị price hợp lệ nên Agent trả lời đúng với sản phẩm electronics có giá cao nhất. |
| Garbage Data (`garbage_data.csv`) | Agent: Based on my data, the best choice is Nuclear Reactor at $999999. | 2 | Agent bị đánh lừa bởi outlier giá cực lớn và không có bước kiểm tra tính hợp lý của sản phẩm trong bộ dữ liệu rác. |

---

## 2. Phân tích & nhận xét

### Tại sao Agent trả lời sai khi dùng Garbage Data?

Khi dùng `garbage_data.csv`, Agent trả lời sai vì chất lượng dữ liệu đầu vào rất kém. Bộ dữ liệu có `duplicate IDs` làm giảm độ tin cậy của bản ghi, có `wrong data types` như giá trị `ten dollars` trong cột `price` khiến việc so sánh và xử lý giá trở nên không ổn định. Ngoài ra, `outlier` như `Nuclear Reactor` với giá `999999` làm logic chọn sản phẩm giá cao nhất bị lệch hoàn toàn. Bản ghi cuối cùng còn có `null value` ở `id` và `category`, cho thấy dữ liệu thiếu và không đầy đủ. Khi Agent dựa trên dữ liệu rác, nó vẫn tìm thấy một bản ghi thuộc nhóm `electronics`, nhưng do không có bước validation và ràng buộc business, nó chọn sản phẩm vô lý thay vì sản phẩm thực sự phù hợp.

---

## 3. Kết luận

**Quality Data > Quality Prompt?** (Đồng ý hay không? Giải thích ngắn gọn.)

Đồng ý. Prompt có tốt đến đâu thì Agent vẫn phụ thuộc vào dữ liệu mà nó đọc được. Nếu dữ liệu sai, thiếu, trùng lặp hoặc có outlier bất thường thì câu trả lời vẫn sẽ sai hoặc gây hiểu nhầm. Vì vậy, dữ liệu chất lượng cao là nền tảng quan trọng hơn để Agent trả lời đúng và đáng tin cậy.
