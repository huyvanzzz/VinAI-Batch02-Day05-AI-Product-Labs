# Synthesis Decision — Từ Evidence Đến Build Slice

## 1. Gom evidence thành cụm

- `Khoản chi ngoài MoMo vẫn nhập tay nhiều`
- `AI có thể gán sai nhưng không nói là nó không chắc`
- `App quá nhiều thứ nên user khó tập trung vào task quản lý chi tiêu`
- `User muốn bắt đầu quản lý tiền nhưng lười và không biết bắt đầu từ đâu`

## 2. Insight

```text
User đã dùng MoMo để thanh toán không chỉ cần thêm một dashboard chi tiêu.
Họ thật ra cần một cách ghi và sửa khoản chi thật nhẹ,
vì nếu danh mục sai hoặc flow quá nhiều bước thì họ bỏ luôn việc theo dõi tài chính.
```

## 3. Opportunity

```text
Cơ hội là dùng AI để gợi ý 2-3 danh mục cho khoản chi mơ hồ ngoài MoMo,
giúp user ghi chép nhanh nhưng vẫn kiểm soát được kết quả,
trong khi giảm risk bằng confidence và one-tap correction.
```

## 4. Chọn build slice

| Câu hỏi | Trả lời |
|---|---|
| User cụ thể chưa? | Có. Người đã dùng MoMo hằng ngày nhưng chưa theo dõi tốt khoản chi ngoài MoMo. |
| Task đủ hẹp chưa? | Có. Chỉ tập trung vào một flow: nhập khoản chi mơ hồ và gán danh mục. |
| AI decision rõ chưa? | Có. AI chỉ làm một việc: gợi ý danh mục có confidence. |
| Failure path rõ chưa? | Có. Case mơ hồ như "linh tinh 120k" hoặc "thuốc và đồ ăn 280k". |
| Có evidence không? | Có. Từ MoMo public page, App Store review, Reddit discussion và analog sản phẩm khác. |

## 5. Quyết định scope

| Tình huống | Quyết định |
|---|---|
| Ý tưởng ban đầu quá rộng | Giữ domain tài chính, cắt xuống một flow phân loại khoản chi. |
| Rủi ro trust cao | Chọn augmentation thay vì automation. |
| Không demo được cả app trong 1 ngày | Bỏ hết phần tư vấn tài chính dài hạn, chỉ giữ một interaction ngắn 3-5 phút. |

## 6. Câu chốt cuối

```text
Dựa trên evidence về friction khi ghi khoản chi ngoài MoMo và thiếu recovery path khi AI không chắc,
nhóm sẽ build một prototype gợi ý danh mục cho khoản chi mơ hồ,
cho user đang muốn theo dõi thu chi nhưng ngại nhập tay,
để giải quyết pain "ghi chép nặng và báo cáo dễ sai",
bằng cách AI gợi ý 2-3 danh mục có confidence,
và sẽ test failure path với các mô tả mơ hồ hoặc mixed-purpose.
```

## 7. Backlog

Những thứ **không build trong Day 06**:

- Tư vấn tài chính cá nhân dài hạn
- Tự động cân đối ngân sách theo tháng
- Gợi ý đầu tư, tiết kiệm hoặc vay vốn
- Đồng bộ mọi nguồn giao dịch ngoài MoMo
