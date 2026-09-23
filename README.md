# LAB 3 - NHẬN DIỆN VÀ ỨNG PHÓ CÁC MỐI ĐE DỌA ĐẾN AN TOÀN THÔNG TIN

## 1. Thông tin sinh viên

- **Họ và tên:** Phạm Gia Bảo
- **MSSV:** 1150080043
---

## 2. Mục tiêu bài thực hành

Bài thực hành nhằm tìm hiểu và nhận diện các mối đe dọa phổ biến đối với hệ thống thông tin, đồng thời làm quen với quy trình phát hiện và ứng phó sự cố.

Các nội dung chính:

- Phân biệt Asset, Vulnerability, Threat, Risk và Attack.
- Nhận diện các nhóm nguồn đe dọa.
- Quan sát và thu thập bằng chứng liên quan đến các tình huống an toàn thông tin.
- Làm quen với Windows Defender, Windows Event Log, Sysmon, Autoruns, Process Explorer và Wireshark.
- Thực hiện theo quy trình:
  **Baseline → Observe → Detect → Contain → Recover → Verify**.

---

## 3. Môi trường thực hành

### Máy Host

- **Hệ điều hành:** Ubuntu Linux
- **Phần mềm ảo hóa:** Oracle VirtualBox 7.2.6

### Máy ảo

- **Hệ điều hành:** Windows 11 Pro
- **CPU:** 2 vCPU
- **RAM:** 6 GB
- **Disk:** 80 GB
- **Network:** Host-only Adapter
- **Host-only network:** `vboxnet0`
- **TPM:** TPM 2.0
- **EFI / Secure Boot:** Enabled

### Phiên bản Windows hiện tại

- **Windows 11 Pro**
- **Version:** 24H2
- **OS Build:** 26100.1

> Lưu ý: môi trường hiện tại chưa đạt đúng phiên bản Windows 11 25H2 theo cấu hình khuyến nghị của bài LAB.

---

## 4. Cách dựng môi trường

1. Cài đặt Oracle VirtualBox trên Ubuntu.
2. Tạo máy ảo Windows 11.
3. Cấu hình máy ảo:
   - 2 CPU
   - 6 GB RAM
   - 80 GB ổ đĩa
   - TPM 2.0
   - EFI và Secure Boot
4. Cấu hình Network Adapter ở chế độ **Host-only Adapter**.
5. Sử dụng `vboxnet0` làm mạng Host-only.
6. Cài đặt Windows 11 Pro trên máy ảo.
7. Kiểm tra phiên bản Windows bằng `winver`.
8. Tạo snapshot trước khi thực hiện các thay đổi lớn trên máy ảo.

Snapshot đã tạo:

`Before_25H2_Update`

---

## 5. Các tình huống thực hiện

| Nội dung | Trạng thái |
|---|---|
| Tạo máy ảo Windows 11 | PASS |
| Cấu hình CPU/RAM/Disk | PASS |
| Cấu hình Host-only Network | PASS |
| Cài đặt Windows 11 Pro | PASS |
| Kiểm tra phiên bản Windows | PASS |
| Tạo snapshot trước khi cập nhật | PASS |
| Windows 11 25H2 theo yêu cầu LAB | CHƯA HOÀN THÀNH |
| Kiểm tra Windows Defender / Firewall | CHƯA HOÀN THÀNH |
| EICAR / Protection History | CHƯA HOÀN THÀNH |
| Windows Event Log | CHƯA HOÀN THÀNH |
| Sysmon | CHƯA HOÀN THÀNH |
| Autoruns | CHƯA HOÀN THÀNH |
| Process Explorer | CHƯA HOÀN THÀNH |
| Wireshark / HTTP / TLS | CHƯA HOÀN THÀNH |

---

## 6. Lỗi gặp phải và cách khắc phục

### 6.1 Không tải được Windows 11 trực tiếp

Trong quá trình chuẩn bị môi trường, việc tải Windows 11 từ nguồn Microsoft gặp vấn đề truy cập.

**Hướng xử lý:**

- Sử dụng UUP dump để lấy các gói Windows cần thiết.
- Tạo bộ cài Windows 11 để cài đặt máy ảo.

### 6.2 Phiên bản Windows chưa đúng yêu cầu LAB

Sau khi cài đặt, kết quả `winver`:

- Windows 11 Pro
- Version 24H2
- OS Build 26100.1

Trong khi môi trường LAB yêu cầu Windows 11 25H2.

**Hướng xử lý:**

Đã tải các gói cập nhật Windows và tạo snapshot:

`Before_25H2_Update`

trước khi thử quá trình nâng cấp.

### 6.3 Máy ảo boot vào Windows Setup

Trong quá trình thử nâng cấp, máy ảo khởi động vào bộ cài Windows và hiển thị màn hình chọn phân vùng cài đặt.

**Cách khắc phục:**

- Không format hoặc xóa partition.
- Eject file ISO khỏi Optical Drive của VirtualBox.
- Khởi động lại máy ảo.
- Windows cũ khởi động lại bình thường.

### 6.4 VirtualBox Guest Additions

Shared Folder chưa xuất hiện trong Windows do Guest Additions chưa được cài đặt.

Khi chọn tải Guest Additions từ VirtualBox, quá trình tải gặp lỗi certificate.

**Trạng thái:** Chưa hoàn thành.

---

## 7. Evidence

Các ảnh chụp và bằng chứng của quá trình thực hành được lưu trong thư mục:

`evidence/`

Các output và log đã được làm sạch được lưu trong:

`logs/`

Danh sách SHA-256 của evidence được lưu trong:

`evidence_sha256.csv`

---

## 8. Kết quả

Môi trường Windows 11 trên VirtualBox đã được tạo và cấu hình cơ bản.

Một số yêu cầu của LAB 3 chưa hoàn thành, đặc biệt là quá trình cập nhật Windows 11 lên phiên bản 25H2 và các tình huống thu thập evidence.

Các nội dung chưa hoàn thành được ghi rõ trong README và sẽ được bổ sung khi tiếp tục thực hành.

---
- Không thêm Defender exclusion.
- Không upload file bị Defender quarantine.
- Không upload installer hoặc executable của Sysinternals, Wireshark và Python.
