---
title: "Worklog Tuần 11"
date: "2025-11-11"
weight: 2
chapter: false
pre: " <b> 1.11. </b> "
---

### Mục tiêu tuần 11:

- Triển khai Business Logic cho chấm công và quy trình duyệt phép.
- Phát triển API Attendance (chấm công) và tích hợp Lambda.
- Xây dựng API Leave Management (quản lý nghỉ phép).

### Các công việc cần triển khai trong tuần này:

| Thứ | Nội dung Học/Research                                                                                    | Công việc Thực hành & Code                                                                                                | AWS Event đã xem                             |
| --- | -------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------- |
| 2   | Business Logic Implementation: Phân tích quy tắc chấm công (check-in/check-out) và quy trình duyệt phép. | Thiết kế database schema cho Attendance và Leave Management.                                                              | Building Serverless Applications with Lambda |
| 3   | Attendance Rules: Xác định business rules cho chấm công (giờ làm việc, late, early leave).               | Phát triển API Attendance: Xây dựng API GET /api/v1/attendance và GET /api/v1/attendance/range.                           |                                              |
| 4   | Update Attendance: Logic cập nhật và chỉnh sửa bản ghi chấm công.                                        | Hoàn thành API PUT /api/v1/attendance/{recordId} để cập nhật thông tin chấm công.                                         |                                              |
| 5   | API Tích hợp Serverless (Lambda): Tìm hiểu cách Lambda xử lý các sự kiện POST/STOP cho chấm công.        | API Chấm công (Lambda Flow): Xây dựng POST /api/attendance/start và POST /api/attendance/stop (Giả định Lambda/DynamoDB). |                                              |
| 6   | Leave Management System: Thiết kế quy trình nghỉ phép (request, approve, reject).                        | Triển khai API Nghỉ phép: Xây dựng GET /api/v1/leaves, GET /api/v1/leaves/history/{employeeId}, và POST /api/v1/leaves.   |                                              |
| 7   | Leave Approval Workflow: Logic duyệt/từ chối đơn nghỉ phép cho Admin.                                    | Hoàn thành API PUT /api/v1/leaves/{id}/approve và PUT /api/v1/leaves/{id}/reject.                                         |                                              |

### Kết quả đạt được tuần 11:

- Hiểu rõ về **Business Logic Implementation**:

  - Phân tích quy tắc chấm công (check-in/check-out)
  - Xác định quy trình duyệt phép (request → approve/reject)
  - Thiết kế database schema phù hợp

- Thành công trong việc phát triển **API Attendance**:

  - GET /api/v1/attendance - Lấy danh sách bản ghi chấm công
  - GET /api/v1/attendance/range - Lấy chấm công theo khoảng thời gian
  - PUT /api/v1/attendance/{recordId} - Cập nhật bản ghi chấm công

- Nắm được **Serverless Architecture với Lambda**:

  - Hiểu cách Lambda xử lý sự kiện real-time
  - Tích hợp Lambda với DynamoDB cho tốc độ cao
  - Thiết kế event-driven architecture

- Triển khai thành công **API Chấm công (Lambda Flow)**:

  - POST /api/attendance/start - Bắt đầu ca làm việc
  - POST /api/attendance/stop - Kết thúc ca làm việc
  - Sử dụng Lambda/DynamoDB cho hiệu năng tối ưu

- Xây dựng hoàn chỉnh **Leave Management System**:

  - GET /api/v1/leaves - Lấy danh sách đơn nghỉ phép
  - GET /api/v1/leaves/history/{employeeId} - Lịch sử nghỉ phép của nhân viên
  - POST /api/v1/leaves - Tạo đơn xin nghỉ phép mới

- Triển khai **Leave Approval Workflow**:

  - PUT /api/v1/leaves/{id}/approve - Duyệt đơn nghỉ phép
  - PUT /api/v1/leaves/{id}/reject - Từ chối đơn nghỉ phép
  - Implement notification system cho approval flow

- Áp dụng **Best Practices**:

  - Validation và error handling cho business logic
  - Transaction management cho các operations phức tạp
  - Audit logging cho attendance và leave records

- Tham gia AWS Event:
  - Building Serverless Applications with Lambda - Áp dụng lý thuyết Serverless cho chấm công real-time
