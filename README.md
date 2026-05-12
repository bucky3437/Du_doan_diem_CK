# Dự Đoán Điểm Cuối Kỳ

Chương trình dự đoán điểm cuối kỳ dựa trên điểm giữa kỳ, sử dụng thuật toán k-NN Regression.

## Phương pháp

- Sắp xếp dataset theo điểm giữa kỳ bằng **MergeSort** — O(n log n)
- Tìm vị trí gần nhất bằng **Binary Search** — O(log n)
- Lấy k = 5 điểm láng giềng gần nhất, tính trung bình điểm cuối kỳ — O(k)

Công thức: `ŷ = (1/k) × Σ yᵢ`, với i thuộc tập k láng giềng gần nhất

## Cấu trúc

```
├── TRAIN2.xlsx          # Dataset 515 mẫu (điểm giữa kỳ, điểm cuối kỳ)
├── train_knn.ipynb      # Notebook huấn luyện, xuất ra model_knn.json
├── model_knn.json       # Kết quả huấn luyện (mảng đã sort + k)
└── demo.html            # Giao diện dự đoán, đọc model_knn.json
```

## Cách chạy

**Bước 1 — Huấn luyện:**
Mở `train_knn.ipynb` trên Jupyter hoặc Google Colab, chạy toàn bộ cell. File `model_knn.json` sẽ được tạo ra.

**Bước 2 — Demo:**
Đặt `demo.html` và `model_knn.json` cùng thư mục, mở bằng Live Server (VS Code) hoặc chạy lệnh:
```
python -m http.server 8000
```
Sau đó truy cập `http://localhost:8000/demo.html`

## Kết quả

| Chỉ số | Giá trị |
|--------|---------|
| R²     | 0.99998 |
| MAE    | 0.00786 |
| RMSE   | 0.01058 |
