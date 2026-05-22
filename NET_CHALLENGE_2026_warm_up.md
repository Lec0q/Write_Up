## 1. TheSLientLeak.pcap: Rò rỉ qua HTTP POST
**Dấu hiệu:** Traffic outbound lạ vào ban đêm thường sử dụng các giao thức phổ biến như HTTP để qua mặt tường lửa.

**Các bước thực hiện:**
1. **Phân tích yêu cầu HTTP:** Ta sử dụng `tshark` để lọc ra các phương thức `POST` (thường dùng để gửi dữ liệu lên server).
   ```bash
   tshark -r TheSLientLeak.pcap -Y 'http.request.method == "POST"' -T fields -e http.request.uri -e urlencoded-form.value
   ```
2. **Phát hiện:** Tại URI `/api/sync`, có tham số `data` chứa chuỗi: `<REDACTED>`.
3. **Giải mã:** Dấu `=` ở cuối là đặc trưng của Base64.
   ```bash
   echo "<REDACTED>" | base64 -d
   ```
**Flag:** `<REDACTED>`

---

## 2. GhostResolver.pcap: Bóng ma DNS Tunneling
**Dấu hiệu:** Quá nhiều truy vấn DNS vào các tên miền lạ và không có phản hồi (Non-existent domain).

**Các bước thực hiện:**
1. **Trích xuất tên miền:** Kẻ tấn công thường giấu dữ liệu trong `subdomain`.
   ```bash
   tshark -r GhostResolver.pcap -Y 'dns.flags.response == 0' -T fields -e dns.qry.name | uniq
   ```
2. **Phát hiện:** Ta thấy các chuỗi ký tự không có nghĩa nhưng có vẻ được chia thành từng đoạn. Quan sát kỹ thấy chúng chỉ gồm chữ cái và số từ 2-7, đây là đặc trưng của **Base32**.
3. **Ghép nối và giải mã:**
   - `<REDACTED>` -> `<REDACTED>`
   - `<REDACTED>` -> `<REDACTED>`
   - `<REDACTED>` -> `<REDACTED>`
**Flag:** `<REDACTED>`

---

## 3. 3AM.pcap: Metadata ẩn trong FTP
**Dấu hiệu:** Giao thức FTP truyền dữ liệu không mã hóa, rất dễ bị bắt gói tin.

**Các bước thực hiện:**
1. **Theo dõi phiên FTP:** Tìm xem có file nào được truyền đi không.
   ```bash
   tshark -r 3AM.pcap -Y 'ftp' -T fields -e ftp.request.command -e ftp.request.arg
   ```
2. **Phát hiện:** User `Duck4705` đã dùng lệnh `STOR` để tải lên file `secret_report.png`.
3. **Trích xuất file:** Tìm luồng TCP tương ứng với file ảnh này (Stream 26) và chuyển về file gốc.
   ```bash
   tshark -r 3AM.pcap -q -z follow,tcp,raw,26 | xxd -r -p > secret_report.png
   ```
4. **Kiểm tra Metadata:** Thông thường flag có thể giấu trong phần Comment của ảnh.
   ```bash
   strings secret_report.png | grep NET{
   ```
**Flag:** `<REDACTED>`

---

## 4. BokenPipe.pcap: Reassembling TCP Stream
**Dấu hiệu:** Traffic không theo giao thức chuẩn (Data thô).

**Các bước thực hiện:**
1. **Đọc dữ liệu thô:** Chuyển đổi dữ liệu trong các gói tin TCP từ Hex sang ASCII để tìm từ khóa.
   ```bash
   tshark -r BokenPipe.pcap -Y 'tcp.len > 0' -T fields -e data | xxd -r -p
   ```
2. **Phát hiện:** Có các chuỗi đánh dấu `PART_1`, `PART_2`,... nằm rải rác.
3. **Ghép flag:**
   - `PART_1:<REDACTED>`
   - `PART_2:<REDACTED>`
   - `PART_3:<REDACTED>`
   - `PART_4:<REDACTED>`
   - `PART_5:<REDACTED>`
**Flag:** `<REDACTED>`

---

## 5. OldDog.pcap: Telnet Plaintext
**Dấu hiệu:** Telnet là "món quà" cho các nhà phân tích vì nó không mã hóa.

**Các bước thực hiện:**
1. **Follow TCP Stream:** Xem toàn bộ nội dung cuộc hội thoại.
   ```bash
   tshark -r OldDog.pcap -q -z follow,tcp,ascii,120
   ```
2. **Phát hiện:** Trong quá trình đăng nhập, kẻ tấn công đã nhập flag vào trường Password.
   ```text
   Password: <REDACTED>
   ```
**Flag:** `<REDACTED>`

