# Thin SPEC Cuối Day 05 — MoMo Quản Lý Chi Tiêu

## 1. Track, product/app và user

**Track:** `Fintech / Personal finance`  
**Product/app thật:** `MoMo - Quản Lý Chi Tiêu / Trợ lý chi tiêu AI`  
**User cụ thể:** `Người đã dùng MoMo để thanh toán hằng ngày nhưng vẫn có nhiều khoản chi ngoài MoMo hoặc mô tả giao dịch mơ hồ, nên báo cáo chi tiêu chưa đáng tin`  
**Nhóm có phải user thật không? Nếu không, khác ở đâu?**  
`Có thể là proxy user một phần. Nếu nhóm không dùng MoMo đủ thường xuyên, khác biệt chính là tần suất phát sinh giao dịch ngoài MoMo và mức độ quan tâm tới báo cáo tháng.`

## 2. Evidence summary

| Evidence | Nguồn | User/pain nói lên điều gì? | SPEC phải đổi gì? |
|---|---|---|---|
| Trang tính năng hứa AI ghi chép, phân loại, báo cáo và hỗ trợ qua chat. | [MoMo - Quản Lý Chi Tiêu](https://www.momo.vn/quan-ly-chi-tieu) | Nhu cầu thật là "bắt đầu dễ, ít nhập tay". | Giữ domain chi tiêu, nhưng buộc slice phải cực nhẹ và rõ giá trị. |
| Flow giao dịch ngoài MoMo vẫn cần nhập tiền, chọn danh mục, chọn thời gian thủ công. | [MoMo - Quản Lý Chi Tiêu](https://www.momo.vn/quan-ly-chi-tieu) | Pain nằm ở chỗ AI chưa giảm đủ ma sát cho off-platform spending. | Đổi build slice sang khoản chi ngoài MoMo. |
| Review/App discussion nói app có quá nhiều thứ, dễ gây rối cho user chỉ muốn làm một task nhanh. | [App Store](https://apps.apple.com/us/app/momo-tr%E1%BB%A3-th%E1%BB%A7-t%C3%A0i-ch%C3%ADnh-v%E1%BB%9Bi-ai/id918751511), [Reddit](https://www.reddit.com/r/VietNam/comments/13tvu0k/what_are_your_opinion_on_mobile_payment_apps_like/) | User cần trust và flow ngắn, không cần thêm một chatbot rộng hơn. | Chọn augmentation, không chọn automation hay assistant quá rộng. |

## 3. Pain statement

```text
User đã dùng MoMo hằng ngày đang gặp khó ở bước ghi và phân loại các khoản chi ngoài MoMo hoặc mô tả giao dịch mơ hồ,
vì flow hiện tại vẫn cần nhập tay khá nhiều và AI chưa cho thấy low-confidence path rõ ràng,
dẫn tới báo cáo chi tiêu sai hoặc user bỏ luôn việc theo dõi tài chính.
Bằng chứng chính là trang tính năng public của MoMo hứa AI hỗ trợ mạnh nhưng flow ngoài MoMo vẫn thủ công, cộng với phản hồi công khai về độ rối của app.
```

## 4. Build slice

```text
Cho user đang ghi một khoản chi mơ hồ ngoài MoMo,
prototype sẽ dùng AI để gợi ý 2-3 danh mục phù hợp kèm confidence ngắn,
tạo ra một giao dịch đã được phân loại và lưu vào báo cáo chi tiêu,
và xử lý trường hợp AI không chắc bằng cách cho user chọn lại 1 chạm hoặc nhập danh mục thủ công.
```

## 5. Auto/Aug decision

Chọn một:

- [x] **Augmentation:** AI gợi ý/draft/phân loại, user quyết cuối.
- [ ] **Conditional automation:** AI tự làm trong case hẹp; case mơ hồ/rủi ro chuyển người.
- [ ] **Automation:** AI tự quyết và tự hành động.

**Lý do chọn:**  
`Danh mục chi tiêu ảnh hưởng trực tiếp đến trust của user với báo cáo tài chính. Sai một vài lần là user ngừng dùng. Vì vậy AI nên gợi ý nhanh chứ không nên auto-quyết trong case mơ hồ.`  

**Human role:** `decider / reviewer / trainer`

## 6. Four paths

| Path | Prototype phải thể hiện gì? |
|---|---|
| Happy | User nhập "Ăn trưa 65k", AI gợi ý đúng `Ăn uống`, user bấm xác nhận, giao dịch được lưu. |
| Low-confidence | User nhập "Linh tinh 120k", AI nói chưa chắc và đưa 2-3 danh mục như `Mua sắm`, `Sinh hoạt`, `Khác`. |
| Failure | User nhập khoản mixed-purpose như "Thuốc và đồ ăn 280k", AI gợi ý sai hoặc confidence thấp. |
| Correction | User đổi lại danh mục đúng, hệ thống ghi nhận correction để lần sau xếp hạng gợi ý tốt hơn. |

## 7. Failure mode nguy hiểm nhất

```text
Nếu user nhập một khoản chi mơ hồ hoặc mixed-purpose,
AI có thể gán sai danh mục nhưng vẫn tỏ ra rất chắc chắn,
hậu quả là báo cáo tháng và cảnh báo ngân sách trở nên sai, làm user mất trust vào toàn bộ tính năng.
Prototype sẽ xử lý bằng ask again + show top 3 options + cho phép sửa ngay + fallback nhập tay.
Owner kiểm thử path này là [Tên thành viên phụ trách test].
```

## 8. Owner plan cho sáng Day 06

| Thành viên | Việc phụ trách | Bằng chứng cần có trong repo |
|---|---|---|
| `[Tên 1]` | Research / evidence | Evidence pack có link, quote/paraphrase và insight chốt |
| `[Tên 2]` | SPEC | Thin spec v1, build slice, auto/aug decision |
| `[Tên 3]` | Prototype | Flow demo hoặc wireframe cho happy + low-confidence |
| `[Tên 4]` | Test / failure path | Bộ test case mơ hồ, mixed-purpose và expected behaviors |
| `[Tên 5]` | Demo script / repo | Script demo 3 phút, file repo gọn và nhất quán |
