# OpenClaw của tôi 🦞

Tài liệu cá nhân, viết cho hoàn cảnh của riêng tôi: người mới bắt đầu, dùng **Windows**, **RAM 8 GB**, ưu tiên **miễn phí**, cần hướng dẫn **từng bước**.

> Nguồn: README chính thức của OpenClaw (https://github.com/openclaw/openclaw). Bản dịch đầy đủ nằm ở file `README.vi.md`.

---

## 1. OpenClaw là gì (nói ngắn gọn)

Một trợ lý AI mã nguồn mở chạy **trên máy của tôi**. Nó có thể nói chuyện với tôi qua Control UI trên máy, hoặc qua các ứng dụng nhắn tin như Telegram, Discord, WhatsApp… Dữ liệu, bộ nhớ và thông tin đăng nhập nằm trên máy tôi.

Điểm quan trọng về tiền bạc:

- **Bản thân OpenClaw miễn phí**: README nói rõ không có gói trả phí, không có dịch vụ lưu trữ riêng, không có token.
- **Nhưng "bộ não" (mô hình AI) là chuyện khác.** OpenClaw cần kết nối tới một mô hình (Claude, Codex, mô hình chạy cục bộ…). Một số nhà cung cấp tính phí theo lượng dùng.

## 2. Quy tắc của tôi (đọc trước khi làm bất cứ gì)

- [ ] **Không nhập thẻ, không mua API, không đăng ký gói trả phí** khi tôi chưa chủ động đồng ý.
- [ ] Ở bước chọn mô hình, nếu một lựa chọn đòi API key có tính phí hoặc đòi thẻ thì **dừng lại**, chưa làm tiếp.
- [ ] Khi trình cài đặt hỏi điều gì tôi chưa hiểu, chọn mặc định an toàn hoặc hỏi lại trước khi bấm.
- [ ] Chưa kết nối người khác, chưa mở Gateway ra Internet (xem mục 6).

## 3. Máy của tôi và điều cần lưu ý

| Thông tin | Ghi chú |
| --- | --- |
| Hệ điều hành | Windows, được trình cài đặt hỗ trợ trực tiếp bằng PowerShell |
| RAM | 8 GB, chạy được OpenClaw, nhưng **nên tránh chạy mô hình AI cục bộ lớn** trên máy này vì rất dễ chậm hoặc đầy RAM |
| Node.js | Trình cài đặt tự chuẩn bị nếu thiếu, không cần cài tay |

Gợi ý thực tế: với 8 GB RAM, hướng nhẹ nhàng nhất là để mô hình chạy ở nhà cung cấp bên ngoài (đám mây) thay vì tải mô hình về chạy trên máy. Việc đó có thể phát sinh chi phí tùy nhà cung cấp, nên mục 2 là bắt buộc.

## 4. Cài đặt từng bước (Windows)

**Bước 1. Mở PowerShell.**
Bấm nút Start, gõ `PowerShell`, mở "Windows PowerShell".

**Bước 2. Chạy lệnh cài đặt chính thức.**

```powershell
iwr -useb https://openclaw.ai/install.ps1 | iex
```

Lệnh này tải script từ trang chính thức của dự án rồi chạy ngay. Chỉ chạy khi chắc chắn bạn gõ đúng địa chỉ `openclaw.ai`.

**Bước 3. Hoàn tất trình hướng dẫn (onboarding).**
Với bản cài mới, trình cài đặt tự mở trình hướng dẫn. Làm theo từng câu hỏi. Đến phần chọn mô hình thì áp dụng **quy tắc ở mục 2**.

Nếu trình hướng dẫn không tự mở, chạy:

```powershell
openclaw onboard --install-daemon
```

**Bước 4. Kiểm tra mọi thứ chạy chưa.**

```powershell
openclaw gateway status
openclaw dashboard
```

Lệnh thứ hai mở giao diện Control UI. Gửi một tin nhắn thử ở đó. Nếu trợ lý trả lời, cài đặt thành công.

## 5. Lệnh hay dùng

| Việc cần làm | Lệnh |
| --- | --- |
| Xem Gateway đang chạy không | `openclaw gateway status` |
| Mở giao diện điều khiển | `openclaw dashboard` |
| Chạy lại trình hướng dẫn | `openclaw onboard --install-daemon` |
| Duyệt người lạ nhắn tin tới | `openclaw pairing approve <kênh> <mã>` |

## 6. Bảo mật cho người mới

README chính thức nhấn mạnh vài điều tôi cần nhớ:

- Coi mọi tin nhắn gửi đến là **không đáng tin**. Các kênh nhắn riêng sẽ yêu cầu ghép cặp với người lạ, và tôi là người duyệt.
- Công cụ của trợ lý **chạy trực tiếp trên máy tôi** trừ khi tôi cấu hình sandbox. Nghĩa là trợ lý có thể thao tác trên máy thật.
- **Chưa** mở Gateway ra Internet và **chưa** cho người khác dùng chung cho đến khi đọc xong:
  - Hướng dẫn bảo mật: https://docs.openclaw.ai/gateway/security
  - Hướng dẫn sandbox: https://docs.openclaw.ai/gateway/sandboxing

## 7. Quyền riêng tư

Theo README: theo mặc định OpenClaw chỉ kiểm tra phiên bản mỗi ngày. Nội dung tôi nhắn sẽ đi tới nhà cung cấp mô hình và nền tảng chat mà tôi chọn. Nếu muốn tắt kiểm tra phiên bản, đặt `update.checkOnStart: false`.

## 8. Khi gặp sự cố

1. Chạy `openclaw gateway status` để xem Gateway còn sống không.
2. Đọc phần xử lý sự cố: https://docs.openclaw.ai/start/getting-started
3. Xem FAQ: https://docs.openclaw.ai/help/faq
4. Hỏi trên Discord của dự án: https://discord.gg/clawd
5. Chụp ảnh màn hình thông báo lỗi và hỏi lại tôi (Claude) để được giải thích bằng tiếng Việt.

## 9. Ghi chú riêng của tôi

*(điền dần trong lúc dùng)*

- Ngày cài đặt:
- Mô hình đang dùng:
- Kênh chat đã kết nối:
- Điều cần nhớ:

---

*Ghi chú: các chi tiết về gói miễn phí hoặc giá của từng nhà cung cấp mô hình thay đổi theo thời gian và không có trong README, nên tôi cần tự kiểm tra trang của nhà cung cấp trước khi đăng ký.*
