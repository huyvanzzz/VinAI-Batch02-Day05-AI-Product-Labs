<<<<<<< HEAD
# Thin SPEC Cuối Day 05 — MoMo Quản Lý Chi Tiêu

## 1. Track, product/app và user

**Track:** `Fintech / Personal finance`  
**Product/app thật:** `MoMo - Quản Lý Chi Tiêu / Trợ lý chi tiêu AI`  
**User cụ thể:** `Người đã dùng MoMo để thanh toán hằng ngày nhưng vẫn có nhiều khoản chi ngoài MoMo hoặc mô tả giao dịch mơ hồ, nên báo cáo chi tiêu chưa đáng tin`  
**Nhóm có phải user thật không? Nếu không, khác ở đâu?**  
`Có thể là proxy user một phần. Nếu nhóm không dùng MoMo đủ thường xuyên, khác biệt chính là tần suất phát sinh giao dịch ngoài MoMo và mức độ quan tâm tới báo cáo tháng.`
=======
# Thin SPEC Cuối Day 05 — Vinmec Smart Intake & Telehealth Router

Thin SPEC không phải PRD đầy đủ. Đây là bản cam kết đủ rõ để sáng Day 06 nhóm build ngay.

## 1. Track, product/app và user

**Track:**  
Healthcare / Telehealth / Patient Intake

**Product/app thật:**  
Trợ lý ảo VinmecCare và luồng chatbot/đặt lịch khám từ xa.

**User cụ thể:**  
Bệnh nhân hoặc người nhà bệnh nhân lần đầu muốn khám từ xa, có triệu chứng sức khỏe nhưng chưa biết mô tả thế nào cho đủ và chưa biết nên chọn chuyên khoa nào.

**Nhóm có phải user thật không? Nếu không, khác ở đâu?**  
Nhóm có thể đóng vai user trong self-use để test luồng nhập triệu chứng ngắn, nhưng chưa hoàn toàn đại diện cho user thật vì:
- Nhóm hiểu công nghệ hơn user phổ thông.
- Nhóm không nhất thiết đang trong trạng thái mệt/lo lắng như bệnh nhân thật.
- Nhóm có thể biết trước mục tiêu test nên hành vi ít tự nhiên hơn user thật.

Vì vậy, nhóm dùng self-use để quan sát flow hiện tại và bổ sung evidence ngoài nhóm bằng analog/review public trong Evidence Pack; nếu kịp trước M1, nhóm sẽ kiểm nhanh thêm với 1-2 người từng đặt lịch khám online.

---
>>>>>>> 6a0949b3840b5c6cb14a208b20d47d12a251275f

## 2. Evidence summary

| Evidence | Nguồn | User/pain nói lên điều gì? | SPEC phải đổi gì? |
|---|---|---|---|
<<<<<<< HEAD
| Trang tính năng hứa AI ghi chép, phân loại, báo cáo và hỗ trợ qua chat. | [MoMo - Quản Lý Chi Tiêu](https://www.momo.vn/quan-ly-chi-tieu) | Nhu cầu thật là "bắt đầu dễ, ít nhập tay". | Giữ domain chi tiêu, nhưng buộc slice phải cực nhẹ và rõ giá trị. |
| Flow giao dịch ngoài MoMo vẫn cần nhập tiền, chọn danh mục, chọn thời gian thủ công. | [MoMo - Quản Lý Chi Tiêu](https://www.momo.vn/quan-ly-chi-tieu) | Pain nằm ở chỗ AI chưa giảm đủ ma sát cho off-platform spending. | Đổi build slice sang khoản chi ngoài MoMo. |
| Review/App discussion nói app có quá nhiều thứ, dễ gây rối cho user chỉ muốn làm một task nhanh. | [App Store](https://apps.apple.com/us/app/momo-tr%E1%BB%A3-th%E1%BB%A7-t%C3%A0i-ch%C3%ADnh-v%E1%BB%9Bi-ai/id918751511), [Reddit](https://www.reddit.com/r/VietNam/comments/13tvu0k/what_are_your_opinion_on_mobile_payment_apps_like/) | User cần trust và flow ngắn, không cần thêm một chatbot rộng hơn. | Chọn augmentation, không chọn automation hay assistant quá rộng. |
=======
| User nhập câu rất mơ hồ/không thực tế như “sốt 90 độ”, VinmecCare báo hệ tri thức chưa có câu trả lời. | Self-use screenshot: `assets/z7896607630360_e3a20e3a6a34bfaa1355b1cad50e12aa.jpg` | Khi bot không hiểu, user chưa được hướng dẫn sửa câu hỏi hoặc trả lời theo slot. | Thêm low-confidence path: AI hỏi lại để làm rõ thay vì chỉ fallback. |
| User nhập “đau dạ dày, đầy hơi, khó tiêu 2 tuần”, VinmecCare chỉ hỏi tuổi/năm sinh. | Self-use screenshot: `assets/z7896607636913_7888656377b674b5bd0e49de9888968c.jpg` | User đã cung cấp triệu chứng và thời gian, nhưng bot chưa khai thác mức độ, triệu chứng đi kèm, red flag. | Build slot-filling theo triệu chứng, không chỉ hỏi tuổi. |
| User nhập “đau chân 3 ngày nay, chân sưng rất nhiều”, VinmecCare chuyển sang phiếu hỗ trợ/hotline. | Self-use screenshot: `assets/z7896607636913_7888656377b674b5bd0e49de9888968c.jpg` (cùng screenshot với Evidence 02, phần dưới ảnh) | Handoff có tồn tại, nhưng thiếu lý do và thiếu summary cho người thật. | Output phải có draft summary khi handoff hoặc route. |
| User nhập “sốt 40 độ”, VinmecCare đưa hướng dẫn tự chăm sóc như uống thuốc hạ sốt, bù nước, nghỉ ngơi. | Self-use screenshot: `assets/z7896607662162_6ce8c49e91a4f700ab242ef5b4aaba96.jpg` | Red flag chưa được ưu tiên đủ rõ. | Thêm Red Flag Check trước mỗi lượt phản hồi. |
| User nhập “Tôi bị chảy máu tôi phải làm sao”, VinmecCare đưa hướng dẫn xử lý tại nhà trước khi làm rõ mức độ/vị trí. | Self-use screenshot: `assets/z7896607705865_88d2d3f8b44f90a5817df515dccc6332.jpg` | Triệu chứng nguy hiểm/mơ hồ cần hỏi nhanh hoặc handoff trước khi tư vấn. | Failure path phải test case chảy máu/khó thở/sốt cao. |
| Chatbot sức khỏe tham khảo có disclaimer không chẩn đoán và nêu dấu hiệu cần đi khám. | Analog screenshot: `assets/z7896607644500_db0c41f3c7c9b231a876363273f4d2a7.jpg` | Trust cần disclaimer và red flag guidance. | Thêm disclaimer trong UI prototype. |

---
>>>>>>> 6a0949b3840b5c6cb14a208b20d47d12a251275f

## 3. Pain statement

```text
<<<<<<< HEAD
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

=======
User bệnh nhân/người nhà bệnh nhân lần đầu muốn khám từ xa đang gặp khó ở bước mô tả triệu chứng và chọn chuyên khoa,
vì họ thường chỉ nhập triệu chứng ngắn, thiếu dữ kiện và không biết thông tin nào là quan trọng,
dẫn tới bot dễ trả lời chung chung, hỏi chưa đúng trọng tâm, user dễ chọn sai luồng khám, và bác sĩ/nhân viên có thể phải hỏi lại từ đầu khi handoff.
Bằng chứng chính là self-use screenshots cho thấy VinmecCare fallback khi không hiểu, hỏi tuổi/năm sinh khá cứng, chuyển hotline/phiếu hỗ trợ nhưng chưa có summary, và có case red flag như sốt 40 độ/chảy máu vẫn được trả lời theo hướng tư vấn chung.
```

---

## 4. Build slice

```text
Cho bệnh nhân hoặc người nhà bệnh nhân lần đầu muốn khám từ xa nhưng chỉ mô tả triệu chứng rất ngắn,
prototype sẽ dùng AI để hỗ trợ tiếp nhận thông tin: kiểm tra slot còn thiếu, hỏi thêm tối đa 3 câu bằng câu hỏi đồng cảm kèm quick replies,
tạo ra gợi ý 1-2 chuyên khoa/luồng khám từ xa và bản tóm tắt triệu chứng nháp cho bác sĩ,
và xử lý failure mode bỏ sót dấu hiệu nguy hiểm bằng Red Flag Check trước mỗi lượt phản hồi và Emergency Handoff khi cần.
```

---

>>>>>>> 6a0949b3840b5c6cb14a208b20d47d12a251275f
## 5. Auto/Aug decision

Chọn một:

- [x] **Augmentation:** AI gợi ý/draft/phân loại, user quyết cuối.
- [ ] **Conditional automation:** AI tự làm trong case hẹp; case mơ hồ/rủi ro chuyển người.
- [ ] **Automation:** AI tự quyết và tự hành động.

**Lý do chọn:**  
<<<<<<< HEAD
`Danh mục chi tiêu ảnh hưởng trực tiếp đến trust của user với báo cáo tài chính. Sai một vài lần là user ngừng dùng. Vì vậy AI nên gợi ý nhanh chứ không nên auto-quyết trong case mơ hồ.`  

**Human role:** `decider / reviewer / trainer`
=======
Y tế là domain rủi ro cao. AI không nên chẩn đoán, kê đơn hoặc tự quyết định thay bác sĩ/user. AI chỉ nên hỗ trợ thu thập thông tin, phát hiện red flag theo rule, gợi ý chuyên khoa ở mức tham khảo và tạo bản tóm tắt nháp.

**Human role:**
- **User:** xác nhận thông tin, sửa thông tin, quyết định có đặt lịch hay không.
- **Bác sĩ:** đọc/sửa bản tóm tắt, chẩn đoán và tư vấn cuối cùng.
- **Nhân viên hỗ trợ:** tiếp nhận các case low-confidence hoặc cần handoff.
- **AI:** intake assistant, không phải bác sĩ thay thế.

---
>>>>>>> 6a0949b3840b5c6cb14a208b20d47d12a251275f

## 6. Four paths

| Path | Prototype phải thể hiện gì? |
|---|---|
<<<<<<< HEAD
| Happy | User nhập "Ăn trưa 65k", AI gợi ý đúng `Ăn uống`, user bấm xác nhận, giao dịch được lưu. |
| Low-confidence | User nhập "Linh tinh 120k", AI nói chưa chắc và đưa 2-3 danh mục như `Mua sắm`, `Sinh hoạt`, `Khác`. |
| Failure | User nhập khoản mixed-purpose như "Thuốc và đồ ăn 280k", AI gợi ý sai hoặc confidence thấp. |
| Correction | User đổi lại danh mục đúng, hệ thống ghi nhận correction để lần sau xếp hạng gợi ý tốt hơn. |
=======
| Happy | User nhập “Tôi bị đau bụng/đau dạ dày đầy hơi 2 tuần”. AI nhận ra thiếu tuổi, mức độ, triệu chứng đi kèm. AI hỏi thêm tối đa 3 câu bằng quick replies. Khi đủ thông tin và không có red flag, AI gợi ý Nội Tiêu hóa/Khám tổng quát từ xa và tạo summary. |
| Low-confidence | User nhập câu mơ hồ như “Lúc này tôi đang bị tình trạng như thế nào” hoặc “Người cứ lảo đảo”. AI không đoán bệnh, hỏi lại để làm rõ. Nếu vẫn không đủ dữ kiện, AI chuyển sang tư vấn tổng quát/nhân viên hỗ trợ và tạo summary ngắn. |
| Failure | User nhập “Tôi đang bị sốt 40 độ”, “Tôi bị chảy máu”, “khó thở”, hoặc “nôn ra máu”. AI phát hiện red flag, dừng intake thường, không đưa hướng dẫn điều trị chi tiết, hiển thị Emergency Handoff và hotline/cơ sở y tế gần nhất. |
| Correction | User ban đầu nói “Tôi bị sốt”, sau đó sửa “À tôi hỏi cho bé nhà tôi 5 tuổi”. AI cập nhật đối tượng, đổi slot hỏi sang ngữ cảnh trẻ em, kiểm tra red flag lại từ đầu và tạo summary mới. |

---
>>>>>>> 6a0949b3840b5c6cb14a208b20d47d12a251275f

## 7. Failure mode nguy hiểm nhất

```text
<<<<<<< HEAD
Nếu user nhập một khoản chi mơ hồ hoặc mixed-purpose,
AI có thể gán sai danh mục nhưng vẫn tỏ ra rất chắc chắn,
hậu quả là báo cáo tháng và cảnh báo ngân sách trở nên sai, làm user mất trust vào toàn bộ tính năng.
Prototype sẽ xử lý bằng ask again + show top 3 options + cho phép sửa ngay + fallback nhập tay.
Owner kiểm thử path này là [Tên thành viên phụ trách test].
```

=======
Nếu user mô tả triệu chứng có red flag như sốt 40°C, khó thở nặng, đau ngực dữ dội, nôn ra máu, mất ý thức, co giật, chảy máu nhiều hoặc yếu/liệt một bên người,
AI có thể thất bại bằng cách tiếp tục hỏi đáp bình thường hoặc đưa hướng dẫn chăm sóc tại nhà/gợi ý đặt khám từ xa không khẩn cấp,
hậu quả là user có thể trì hoãn xử lý tình huống nguy hiểm.
Prototype sẽ xử lý bằng Red Flag Check trước mỗi lượt phản hồi; nếu chạm red flag thì dừng intake flow, hiển thị Emergency Handoff, khuyến nghị liên hệ cấp cứu/cơ sở y tế gần nhất và không đưa ra chẩn đoán.
Owner kiểm thử path này là Test / failure-path lead.
```

Câu cảnh báo mẫu trong prototype:

```text
Triệu chứng bạn mô tả có thể cần được hỗ trợ y tế khẩn cấp. Trợ lý không thể đánh giá an toàn qua chat trong trường hợp này. Vui lòng liên hệ cấp cứu hoặc đến cơ sở y tế gần nhất ngay khi có thể.
```

---

>>>>>>> 6a0949b3840b5c6cb14a208b20d47d12a251275f
## 8. Owner plan cho sáng Day 06

| Thành viên | Việc phụ trách | Bằng chứng cần có trong repo |
|---|---|---|
<<<<<<< HEAD
| `[Tên 1]` | Research / evidence | Evidence pack có link, quote/paraphrase và insight chốt |
| `[Tên 2]` | SPEC | Thin spec v1, build slice, auto/aug decision |
| `[Tên 3]` | Prototype | Flow demo hoặc wireframe cho happy + low-confidence |
| `[Tên 4]` | Test / failure path | Bộ test case mơ hồ, mixed-purpose và expected behaviors |
| `[Tên 5]` | Demo script / repo | Script demo 3 phút, file repo gọn và nhất quán |
=======
| Research lead | Research / evidence | Ảnh self-use VinmecCare, bảng observation, thêm ít nhất 1 nguồn ngoài nhóm hoặc phỏng vấn nhanh. |
| SPEC lead | SPEC | File `thin-spec.md`, pain statement, build slice, Auto/Aug decision, Four paths. |
| Prototype lead | Prototype | UI chat intake, quick replies, logic slot-filling, màn hình gợi ý chuyên khoa và summary. |
| Test / failure-path lead | Test / failure path | Test đủ 4 paths, đặc biệt red flag case: sốt 40°C, chảy máu, khó thở/nôn ra máu; ghi kết quả test. |
| Demo / repo lead | Demo script / repo | Script demo 3-5 phút, gom file vào repo, kiểm tra cấu trúc nộp bài và assets ảnh. |

---

## Disclaimer trong prototype

```text
Trợ lý AI chỉ hỗ trợ thu thập thông tin và gợi ý hướng đặt lịch. Nội dung không thay thế chẩn đoán hoặc tư vấn y tế của bác sĩ.
```

---

## Definition of Done cho Day 06

Prototype được xem là đạt nếu demo được:

- User nhập triệu chứng ngắn.
- AI hỏi thêm tối đa 3 câu.
- Có quick replies.
- Có red flag handoff.
- Có low-confidence path.
- Có correction path.
- Có gợi ý chuyên khoa/khám từ xa.
- Có bản tóm tắt triệu chứng nháp.
- Có disclaimer rõ ràng.
>>>>>>> 6a0949b3840b5c6cb14a208b20d47d12a251275f
