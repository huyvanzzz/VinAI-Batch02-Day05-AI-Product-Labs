# Evidence Pack — MoMo Quản Lý Chi Tiêu / Trợ Lý Chi Tiêu AI

> Ghi chú: vì repo hiện chưa có screenshot và log self-use thật trong app, bản này dùng walkthrough từ trang public của MoMo + review công khai để dựng một draft nộp bài trung thực. Khi nhóm có ảnh chụp app thật, chỉ cần thay link bằng screenshot là xong.

## 1. Nhóm và track

**Tên nhóm:** `[Điền tên nhóm]`  
**Track:** `Fintech / Personal finance`  
**Product/app đã chọn:** `MoMo - Quản Lý Chi Tiêu / Trợ Lý chi tiêu AI`  
**Build slice đang nghĩ:** `AI gợi ý 2-3 danh mục cho khoản chi mơ hồ ngoài MoMo, có confidence và one-tap correction`

## 2. Self-use evidence

| Observation | Screenshot/link | Path liên quan | Điều học được |
|---|---|---|---|
| MoMo public page hứa AI tự động ghi chép, tự động phân loại, báo cáo tuần/tháng và gợi ý chi tiêu. | [momo.vn/quan-ly-chi-tieu](https://www.momo.vn/quan-ly-chi-tieu) | Happy | Giá trị cốt lõi rất rõ khi giao dịch đủ rõ nghĩa và đã nằm trong hệ sinh thái MoMo. |
| Cùng trên trang đó, flow thêm giao dịch ngoài MoMo vẫn yêu cầu user nhập số tiền, chọn danh mục và thời gian thủ công. | [momo.vn/quan-ly-chi-tieu](https://www.momo.vn/quan-ly-chi-tieu) | Failure / Correction | Lời hứa "AI giúp ghi chép nhẹ tênh" chưa thật sự đúng với khoản chi ngoài MoMo, là chỗ tốt để cắt build slice. |
| FAQ nói AI phân loại dựa vào lịch sử phân loại trước đó, lời nhắn chuyển tiền và dữ liệu AI, nhưng không thấy low-confidence path hay giải thích vì sao danh mục bị gán. | [momo.vn/quan-ly-chi-tieu](https://www.momo.vn/quan-ly-chi-tieu) | Low-confidence / Failure | Risk lớn không phải chỉ là AI sai, mà là AI sai trong im lặng khiến user mất trust vào báo cáo. |

## 3. User / review / social evidence

| Quote / review / observation | Nguồn | User là ai? | Pain/failure mode |
|---|---|---|---|
| Một review App Store năm 2025 mô tả người dùng chỉ muốn thanh toán nhanh nhưng liên tục bị pop-up trong app làm phiền và máy bị lag/nóng. | [App Store MoMo](https://apps.apple.com/us/app/momo-tr%E1%BB%A3-th%E1%BB%A7-t%C3%A0i-ch%C3%ADnh-v%E1%BB%9Bi-ai/id918751511) | User đang dùng MoMo cho tác vụ nhanh | Product quá nhiều thứ, làm mờ core task và giảm khả năng user phát hiện/sửa lỗi phân loại. |
| Một thảo luận công khai trên Reddit về các app thanh toán ở Việt Nam nhận xét MoMo có quá nhiều feature và trở nên rối, khó điều hướng. | [Reddit thread](https://www.reddit.com/r/VietNam/comments/13tvu0k/what_are_your_opinion_on_mobile_payment_apps_like/) | Người dùng ví điện tử/super app | Super-app bloat làm user khó tìm đúng flow cần thiết và tăng cognitive load. |
| Bài viết public của MoMo nói hơn 90% người dùng có nhu cầu quản lý chi tiêu nhưng chỉ 8% thực sự làm được có hệ thống; hai rào cản lớn là lười và không biết bắt đầu từ đâu. | [MoMo blog](https://www.momo.vn/blog/ung-dung-quan-ly-tai-chinh-ca-nhan-pho-bien-nhat-c103dt2282) | Người dùng muốn quản lý chi tiêu nhưng chưa duy trì được thói quen | User không chỉ cần dashboard, họ cần start flow cực nhẹ và ít nhập tay. |

## 4. Competitor / analog evidence

| App / mô hình tham khảo | Họ xử lý task này thế nào? | Pattern học được | Có áp dụng trong 1 ngày không? |
|---|---|---|---|
| [Money Lover](https://moneylover.zendesk.com/hc/en-us/articles/34045598720025-Category-Definition-and-Usage) | Cho user chọn danh mục rõ ràng khi tạo giao dịch và tự chỉnh/tạo category theo nhu cầu. | Với tác vụ tài chính, controllability đôi khi quan trọng hơn "AI làm hết". | Có. Có thể thêm step chọn nhanh 2-3 danh mục thay vì auto-gán cứng. |
| [YNAB](https://support.ynab.com/en_us/categorizing-transactions-a-guide-HyRl60sks) | Hệ thống nhớ category gần nhất nhưng vẫn cho đổi category và tắt auto-categorization cho payee cụ thể. | Automation nên đi kèm cơ chế override rõ và học từ correction. | Có. Dùng cho logic confidence + correction memory. |

## 5. Evidence -> Insight

```text
Evidence nổi bật nhất:
- MoMo hứa AI sẽ ghi chép và phân loại rất nhẹ.
- Nhưng flow khoản chi ngoài MoMo vẫn khá thủ công.
- Nguồn công khai cho thấy user cũng đã mệt với độ phức tạp và nhiễu của super app.

Insight:
User không chỉ gặp vấn đề "chưa có app quản lý chi tiêu".
Thật ra họ cần một cách ghi và sửa khoản chi thật nhanh, đủ tin cậy để báo cáo tháng không bị sai.

Opportunity:
AI có thể giúp bằng cách gợi ý 2-3 danh mục cho khoản chi mơ hồ ngoài MoMo,
cho user sửa 1 chạm và học từ correction đó.
```

## 6. Evidence đổi SPEC như thế nào?

- [ ] Đổi user chính.
- [x] Đổi pain statement.
- [x] Đổi build slice.
- [x] Đổi Auto/Aug decision.
- [x] Đổi 4 paths.
- [x] Đổi failure mode.
- [x] Đổi owner/test plan.

```text
Trước evidence, nhóm định làm "AI assistant quản lý tài chính cá nhân" khá rộng.
Sau evidence, nhóm đổi thành "AI gợi ý danh mục cho khoản chi mơ hồ ngoài MoMo".
Lý do:
1. Đây là chỗ promise và reality lệch nhau rõ nhất.
2. Đây là task đủ nhỏ để demo trong 3-5 phút.
3. Failure path và correction path đều test được trong 1 ngày.
```
