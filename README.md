# -Insight_404-datathon-2026

Repository này chứa toàn bộ mã nguồn, quy trình phân tích và mô hình học máy để giải quyết bài toán Dự báo Doanh thu thuộc khuôn khổ cuộc thi VinTelligence Datathon 2026.

## Cấu trúc thư mục (Repository structure)

Dự án được tổ chức theo luồng công việc tuyến tính, từ dữ liệu thô đến kết quả dự báo cuối cùng:
```text
repository-name
 ┣ 1_data_cleaing.ipynb     # Tiền xử lý, xử lý missing values và làm sạch dữ liệu thô
 ┣ 2_eda.ipynb              # Phân tích Khám phá Dữ liệu (EDA) và tìm kiếm Insights
 ┣ 3_model_baseline.ipynb   # Feature Engineering, Huấn luyện mô hình, Ensemble và Xuất kết quả
 ┣ README.md                # Tài liệu hướng dẫn chạy mã nguồn
 ┗ submission.csv           # File kết quả dự báo doanh thu cuối cùng
```

## Hướng dẫn Chạy lại kết quả (How to reproduce)

**Môi trường khuyến nghị:** Các Notebook trong dự án này được thiết kế để chạy tốt nhất trên **Google Colab**. Các đường dẫn tải dữ liệu (từ Google Drive) và lệnh tự động tải file kết quả đã được cấu hình sẵn bên trong code.

Để tái lập lại kết quả, vui lòng chạy các file Notebook theo đúng thứ tự dưới đây:

### Bước 1: Làm sạch dữ liệu
*   **File thực thi:** `1_data_cleaing.ipynb`
*   **Mô tả:** Notebook này sẽ tự động tải bộ dữ liệu thô từ link Google Drive đã thiết lập sẵn. Sau đó, nó thực hiện các bước làm sạch, loại bỏ nhiễu và xử lý dữ liệu thiếu.
*   **Cách chạy:** Mở file trên Google Colab và chọn `Runtime` -> `Run all`. (Sau bước này, nhóm đã đóng gói dữ liệu sạch thành file zip và upload lên một link Drive mới để dùng cho các bước sau).

### Bước 2: Phân tích khám phá dữ liệu (EDA)
*   **File thực thi:** `2_eda.ipynb`
*   **Mô tả:** Code sẽ tự động tải file dữ liệu đã làm sạch (từ Bước 1) thông qua link Drive được gắn sẵn. Chứa các biểu đồ phân tích xu hướng, tính mùa vụ và mối tương quan giữa các biến.
*   **Cách chạy:** Mở file trên Google Colab và chọn `Runtime` -> `Run all`.

### Bước 3: Huấn luyện mô hình & xuất file dự báo
*   **File thực thi:** `3_model_baseline.ipynb`
*   **Mô tả:** Đây là pipeline chính của dự án. Code sẽ tự động:
    1. Tải dữ liệu sạch và file mẫu `sample_submission.csv` từ Google Drive.
    2. Thực hiện trích xuất đặc trưng (Feature Engineering) bao gồm mã hóa chu kỳ (Cyclical) và Thống kê lịch sử theo thời kỳ (Regime-Segmented Target Encoding).
    3. Huấn luyện và tinh chỉnh (Tuning) các thuật toán: XGBoost, LightGBM, Random Forest.
    4. Tìm tỷ lệ Ensemble tối ưu bằng Weighted Average và áp dụng lên tập Submission.
*   **Cách chạy:** Mở file trên Google Colab và chọn `Runtime` -> `Run all`.
*   **Kết quả:** Sau khi cell cuối cùng chạy xong, trình duyệt sẽ **tự động tải về máy** file `My_Ultimate_Submission.csv` (tương đương với file `submission.csv` có trong repository này).

---

## 🛠️ Công nghệ & thư viện sử dụng
*   **Ngôn ngữ:** Python 3
*   **Xử lý dữ liệu:** Pandas, NumPy
*   **Trực quan hóa:** Matplotlib, Seaborn
*   **Machine Learning:** Scikit-learn, XGBoost, LightGBM
*   **Môi trường:** Google Colab, Google Drive API (`gdown`)
```
