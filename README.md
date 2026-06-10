[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=24112857&assignment_repo_type=AssignmentRepo)
# Day 10 Lab: Data Pipeline & Data Observability

**Student Email:** vankhiem284@gmail.com
**Name:** Le Van Khiem

---

## Mô tả

Bài lab này xây dựng một ETL pipeline đơn giản để đọc dữ liệu từ `raw_data.json`, kiểm tra và loại bỏ các bản ghi không hợp lệ, chuẩn hóa dữ liệu, sau đó lưu kết quả ra file `processed_data.csv`. Ngoài ra, bài lab còn mô phỏng agent trả lời trên dữ liệu sạch và dữ liệu rác để thấy được ảnh hưởng của chất lượng dữ liệu đến độ chính xác của AI.

---

## Cách chạy (How to Run)

### Prerequisites
```bash
pip install pandas
```

Trên macOS/Linux, dùng `python3` nếu máy không có lệnh `python`.

### Chạy ETL Pipeline
```bash
python3 solution.py
```

### Chạy Agent Simulation (Stress Test)
```bash
# Chạy ETL trước để tạo processed_data.csv
python3 solution.py

# Sau đó chạy agent simulation với clean data và garbage data
python3 agent_simulation.py
```

---

## Cấu trúc thư mục

```
├── solution.py              # ETL Pipeline script
├── processed_data.csv       # Output của pipeline
├── experiment_report.md     # Báo cáo thí nghiệm
└── README.md                # File này
```

---

## Kết quả

Pipeline đã xử lý thành công dữ liệu đầu vào và tạo ra file `processed_data.csv`. Tổng cộng có 5 bản ghi ban đầu, trong đó 3 bản ghi hợp lệ được giữ lại và 2 bản ghi không hợp lệ bị loại bỏ trong bước validation. Dữ liệu đầu ra đã được thêm cột `discounted_price`, chuẩn hóa `category` về dạng Title Case, và bổ sung cột `processed_at` để phục vụ observability.
