# Báo cáo benchmark trên r5.2xlarge:

- Do không thể request tăng GPU quota increase trên AWS, em chuyển sang phương án dự phòng dùng CPU instance r5.2xlarge để chạy benchmark LightGBM.
- Dataset Credit Card Fraud Detection có 284,807 dòng được load trong 1.7859 giây. Quá trình training hoàn tất rất nhanh, chỉ mất 1.6690 giây, với best iteration là 58.
- Mô hình đạt AUC-ROC = 0.977386, cho thấy khả năng phân biệt giao dịch gian lận và bình thường khá tốt.
- Accuracy đạt 0.995716, tuy nhiên do dữ liệu mất cân bằng nên F1-score chỉ đạt 0.419048. Recall đạt 0.897959, nghĩa là mô hình phát hiện được phần lớn giao dịch gian lận.
- Tốc độ inference rất nhanh: khoảng 0.9835 ms cho 1 dòng và throughput đạt khoảng 701,428 rows/sec cho batch 1000 dòng.
- Kết quả cho thấy r5.2xlarge đủ mạnh để chạy bài toán ML truyền thống thay thế khi không dùng được GPU.
