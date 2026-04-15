# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** AI20K-XXXX
**Name:** Trần Thanh Phong
**Date:** 15/04/2026

---

## 1. Ket qua thi nghiem

Chay `agent_simulation.py` voi 2 bo du lieu va ghi lai ket qua:

| Scenario | Agent Response | Accuracy (1-10) | Notes |
|----------|----------------|-----------------|-------|
| Clean Data (`processed_data.csv`) | Agent: Based on my data, the best choice is Laptop at $1200. | 9 | Data đã được validate nên kết quả hợp lý |
| Garbage Data (`garbage_data.csv`) | Agent: Based on my data, the best choice is Nuclear Reactor at $999999. | 2 | Bị ảnh hưởng bởi outlier và data lỗi |

---

## 2. Phan tich & nhan xet

### Tai sao Agent tra loi sai khi dung Garbage Data?

Agent trả lời sai khi sử dụng garbage data vì dữ liệu đầu vào chứa nhiều vấn đề về chất lượng. Thứ nhất, tồn tại outlier như sản phẩm "Nuclear Reactor" có giá cực lớn (999999), khiến thuật toán chọn nhầm vì logic chỉ dựa trên giá cao nhất. Thứ hai, có duplicate ID, làm mất tính nhất quán của dữ liệu. Thứ ba, sai kiểu dữ liệu như "ten dollars" gây lỗi tiềm ẩn khi xử lý số. Cuối cùng, giá trị null và thiếu category khiến dữ liệu không đầy đủ. Vì agent không có cơ chế kiểm tra chất lượng dữ liệu, nên các lỗi này trực tiếp dẫn đến kết quả sai lệch.

---

## 3. Ket luan

**Quality Data > Quality Prompt?** (Dong y hay khong? Giai thich ngan gon.)

-> Đồng ý
Dữ liệu chất lượng cao quan trọng hơn prompt vì AI chỉ có thể đưa ra kết quả tốt khi dữ liệu đầu vào đáng tin cậy. Một prompt tốt không thể sửa được dữ liệu sai, trong khi dữ liệu sạch giúp ngay cả logic đơn giản cũng cho kết quả chính xác.