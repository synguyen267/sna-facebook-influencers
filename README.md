# Phân tích cộng đồng và xác định người dùng có tầm ảnh hưởng trên mạng xã hội

Bài tập cá nhân môn **Social Media Network**.
Sinh viên: Nguyễn Tiến Sỹ (MSSV 3122410363) - Giảng viên: Phan Tấn Quốc.

Dự án phân tích mạng bạn bè Facebook (SNAP **ego-Facebook**, 4.039 nút, 88.234 cạnh) để:

1. Phát hiện cấu trúc cộng đồng (Louvain và Label Propagation).
2. Xác định người dùng có tầm ảnh hưởng (Degree, Betweenness, Closeness, PageRank).
3. Kiểm chứng các độ đo bằng mô phỏng lan truyền Independent Cascade.

## Kết quả chính

- Đường đi trung bình 3,69 và hệ số phân cụm 0,61 (đặc trưng small-world).
- Louvain: 16 cộng đồng, modularity 0,8349.
- Label Propagation (10 lần chạy): 66-75 cộng đồng, modularity trung bình 0,8129 ± 0,0024.
- Người dùng ảnh hưởng nhất: nút 107 và 1684 (có mặt trong top 10 của cả 4 độ đo).
- Mô phỏng lan truyền (p = 0,02): PageRank 936 > Betweenness 922 > Degree 891 > Closeness 712 > Ngẫu nhiên 542 nút.

Lưu ý: 10 nút trong top PageRank đều là các nút ego của bộ dữ liệu, nên kết quả về người có ảnh hưởng không nên suy rộng cho toàn Facebook.

## Cấu trúc thư mục

- data/: dữ liệu và kết quả trung gian
- notebooks/01_data_preprocessing.ipynb: đọc dữ liệu, thống kê mô tả mạng
- notebooks/02_community_detection.ipynb: Louvain, Label Propagation, xuất file Gephi
- notebooks/03_influencers.ipynb: độ đo trung tâm, mô phỏng lan truyền
- figures/: hình dùng trong báo cáo

## Dữ liệu

Bộ dữ liệu không nằm trong repo. Tải tệp facebook_combined.txt.gz tại https://snap.stanford.edu/data/ego-Facebook.html và đặt vào thư mục data/ (không cần giải nén).

## Cách chạy lại

Yêu cầu Python 3.10 trở lên.

    pip install -r requirements.txt
    python -m notebook

Chạy lần lượt các notebook theo thứ tự 01, 02, 03 vì notebook sau đọc tệp do notebook trước tạo ra. Hình mạng tô màu theo cộng đồng được vẽ bằng Gephi từ tệp data/facebook_louvain.gexf.

## Công cụ

Python, NetworkX, pandas, NumPy, SciPy, Matplotlib, Jupyter Notebook, Gephi.
