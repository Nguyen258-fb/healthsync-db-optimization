# Báo cáo chẩn đoán lỗ hổng (Gap Analysis Report) - HealthSync

Sau khi đối chiếu giữa Activity Diagram và thiết kế Legacy SQL Script, phát hiện 3 điểm vênh nghiêm trọng sau:
1. **Vòng đời trạng thái lịch hẹn:** Thiết kế cũ dùng cột `is_active` (kiểu Boolean) chỉ biểu diễn được 2 trạng thái (True/False), không thể đáp ứng quy trình 5 trạng thái thực tế: `PENDING`, `CONFIRMED`, `CHECKED_IN`, `COMPLETED`, `CANCELLED`.
2. **Thiếu thông tin tài chính và xử lý hủy lịch:** Hệ thống cũ không có các cột `deposit_amount`, `penalty_fee`, và `cancel_reason`, dẫn đến việc không thể tính toán phí phạt cọc khi bệnh nhân hủy lịch.
3. **Thiếu bảng quản lý Đơn thuốc:** Cấu trúc cũ hoàn toàn vắng mặt bảng `Prescriptions`, khiến Bác sĩ không có nơi để lưu trữ đơn thuốc khi lịch hẹn chuyển sang trạng thái `COMPLETED`.
