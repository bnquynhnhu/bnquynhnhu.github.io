Những phương pháp đánh giá mô hình:
1. SSE: Sum Square Error: tổng bình phương sai lệch giữa giá trị y thực và giá trị dự báo
   SSE = (y1_real - y1_predict)*2 + (y2_real - y2_predict)*2 + ... + (yn_real - yn_predict)*2

   SSE càng nhỏ, mô hình càng tốt
   Hạn chế: Khó xác định được SSE nào là tốt, vì trong trường hợp mẫu dữ liệu càng lớn (n lớn) thì SSE càng lớn. Ngược lại, dữ liệu nhỏ thì SSE càng nhỏ.
   
2. RMSE: Root mean square error
   Sẽ bằng căn bậc hai của SSE/n.
   Không phụ thuộc vào n.
   
3. R2 
   SST: xác định đường baseline, y_mean = (y1 + y2 + ... + yn)/n
   SST = (y1 - y_mean)*2 + (y2 - y_mean)*2 + ... + (yn - y_mean)*2
   
   R2 = 1 - SSE/SST
   R2 = 0: mô hình không tốt
   R2 = 1: mô hình dự báo chính xác hoàn toàn
   Ngược với SSE có giá trị càng nhỏ thì mô hình càng tốt, R2 càng lớn thì mô hình càng chính xác.
   
