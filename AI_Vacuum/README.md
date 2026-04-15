# AI Vacuum - Máy Hút Bụi Thông Minh 🤖

## Mô Tả Dự Án

Dự án **AI Vacuum** là bài tập lớn cho học phần "Nhập môn Trí Tuệ Nhân Tạo". Đây là một ứng dụng mô phỏng máy hút bụi tự động có khả năng di chuyển trên một bảng lưới 2D để tìm kiếm và "hút" các điểm bụi.

Ứng dụng sử dụng các **thuật toán tìm kiếm trong không gian trạng thái** để tìm đường đi tối ưu từ vị trí máy hút bụi đến các vị trí bụi, đồng thời tránh các vật cản.

---

## 🎯 Tính Năng Chính

- **Giao diện đồ họa (GUI)**: Sử dụng Tkinter để hiển thị bảng lưới
- **Sinh ngẫu nhiên bảng**: Tạo bảng với:
  - Vị trí máy hút bụi
  - Vị trí các điểm bụi
  - Vị trí các vật cản
- **Nhiều thuật toán tìm kiếm**:
  - **DFS (Depth-First Search)** - Tìm kiếm theo chiều sâu
  - **BFS (Breadth-First Search)** - Tìm kiếm theo chiều rộng
  - **A\* Algorithm** - Tìm kiếm với heuristic, tối ưu nhất
- **Hiển thị trực quan**: Theo dõi quá trình tìm kiếm của thuật toán theo từng bước

---

## 📁 Cấu Trúc Dự Án

```
AI_Vacuum/
├── main.py                              # File chính - Chương trình GUI
├── intro_to_AI.ipynb                    # Notebook Jupyter giới thiệu
├── README.md                            # File này
├── agorithm/                            # Thư mục chứa các thuật toán
│   ├── A_star_10_12_nearest_first.py   # Thuật toán A* (phiên bản tối ưu)
│   ├── A_star_with_GUI_work.py         # A* với hỗ trợ GUI
│   ├── bfs_AI.py                       # BFS - Phiên bản 1
│   ├── bfs_in_AI.py                    # BFS - Phiên bản 2
│   ├── bfs_in_AI1.py                   # BFS - Phiên bản 3
│   ├── dfs_AI.py                       # DFS - Phiên bản 1
│   ├── dfs_AI1.py                      # DFS - Phiên bản 2
│   ├── dfs_in_AI.py                    # DFS - Phiên bản 3
│   └── ...
└── image/                              # Thư mục chứa hình ảnh
```

---

## 🚀 Hướng Dẫn Sử Dụng

### Yêu Cầu Hệ Thống

- **Python 3.7+**
- **Thư viện cần thiết**:
  ```bash
  pip install pillow tkinter
  ```

### Chạy Ứng Dụng

1. Mở terminal/cmd tại thư mục dự án
2. Chạy lệnh:

   ```bash
   python main.py
   ```

3. **Giao diện sẽ hiển thị**:
   - **Nhập số hàng và cột**: Kích thước bảng lưới
   - **Nhập số vật cản**: Số lượng vật cản trên bảng
   - **Nhập số điểm bụi**: Số lượng điểm bụi cần hút
   - **Chọn thuật toán**: DFS, BFS, hoặc A\*
   - **Xem quá trình**: Theo dõi từng bước tìm kiếm

---

## 📊 Các Thuật Toán Được Triển Khai

### 1. **DFS (Depth-First Search)** 🔴

- Tìm kiếm theo chiều sâu
- Khám phá một nhánh cho đến hết cùng trước khi quay lại
- **Ưu điểm**: Dùng ít bộ nhớ
- **Nhược điểm**: Không đảm bảo tìm đường đi ngắn nhất

### 2. **BFS (Breadth-First Search)** 🔵

- Tìm kiếm theo chiều rộng
- Khám phá tất cả các node ở cùng mức trước khi đi sâu hơn
- **Ưu điểm**: Tìm được đường đi ngắn nhất
- **Nhược điểm**: Dùng nhiều bộ nhớ hơn DFS

### 3. **A\* Algorithm** 🟡

- Sử dụng heuristic (ước lượng) để hướng dẫn tìm kiếm
- Công thức: `f(n) = g(n) + h(n)`
  - `g(n)` = Chi phí thực tế từ điểm bắt đầu đến n
  - `h(n)` = Chi phí ước lượng từ n đến đích
- **Ưu điểm**: Nhanh nhất, tìm được đường đi tối ưu
- **Nhược điểm**: Phức tạp hơn, cần heuristic tốt

---

## 🎮 Hình Thức Biểu Diễn Trên Bảng

| Ký Hiệu | Ý Nghĩa                     |
| ------- | --------------------------- |
| `S`     | Vị trí máy hút bụi hiện tại |
| `X`     | Vật cản không thể đi qua    |
| `.`     | Ô trống đã khám phá         |
| `2`     | Điểm bụi cần hút            |
| `0`     | Ô trống chưa khám phá       |

---

## 📈 So Sánh Hiệu Suất Các Thuật Toán

| Tiêu Chí               | DFS    | BFS    | A\*       |
| ---------------------- | ------ | ------ | --------- |
| Độ phức tạp thời gian  | O(V+E) | O(V+E) | O(h\*(V)) |
| Độ phức tạp không gian | O(h)   | O(V)   | O(V)      |
| Tìm được đường tối ưu  | ❌     | ✅     | ✅        |
| Tốc độ                 | 🟢     | 🟡     | 🟢        |

---

## 💻 Cấu Trúc Code Chính

### main.py

```
- random_matrix(): Sinh bảng ngẫu nhiên
- create_table(): Tạo giao diện bảng lưới
- run_algorithm(): Chạy thuật toán đã chọn
- visualize_path(): Hiển thị đường đi
```

### Các file thuật toán

Mỗi file thuật toán chứa:

- `initialize_*()`: Khởi tạo tham số cần thiết
- `*()`: Hàm chính thực hiện tìm kiếm
- `check()`: Kiểm tra vị trí hợp lệ
- `new_position()`: Cập nhật vị trí mới

---

## 🔧 Các Phiên Bản Khác Nhau

- **Phiên bản 1, 2, 3**: Các biến thể khác nhau của cùng một thuật toán
- **Phiên bản tối ưu**: Được chọn lọc để sử dụng tốt nhất cho giao diện GUI

---

## 📝 Lưu Ý

- Thuật toán A\* yêu cầu heuristic tốt (thường dùng heuristic Manhattan hoặc Euclidean)
- Kích thước bảng ảnh hưởng lớn đến hiệu suất
- Số lượng vật cản cũng ảnh hưởng đến độ khó của bài toán

---

## 👨‍💻 Tác Giả & Liên Hệ

Bài tập lớn học phần **Nhập môn Trí Tuệ Nhân Tạo**

---

## 📚 Tài Liệu Tham Khảo

- [DFS - Wikipedia](https://en.wikipedia.org/wiki/Depth-first_search)
- [BFS - Wikipedia](https://en.wikipedia.org/wiki/Breadth-first_search)
- [A\* Search Algorithm - Wikipedia](https://en.wikipedia.org/wiki/A*_search_algorithm)
- [Artificial Intelligence: A Modern Approach](https://aima.cs.berkeley.edu/)

---

**Cập nhật lần cuối**: April 2026
