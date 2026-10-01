Câu 1: Trình bày sự khác nhau giữa Value Types (Kiểu giá trị) và Reference Types
(Kiểu tham chiếu) trong C# về cơ chế lưu trữ vùng nhớ (Stack vs Heap).

Đặc điểm	Value Types (Kiểu giá trị)	Reference Types (Kiểu tham chiếu)
Vùng nhớ lưu trữ	Lưu trực tiếp giá trị trên Stack.	Lưu địa chỉ tham chiếu trên Stack, dữ liệu thực tế nằm trên Heap.
Các kiểu dữ liệu	int, float, bool, char, struct, enum...	class, interface, string, object, mảng (array)...
Khi gán biến	Sao chép toàn bộ giá trị sang vùng nhớ mới.	Sao chép địa chỉ tham chiếu, hai biến cùng trỏ vào một vùng dữ liệu.
Quản lý bộ nhớ	Tự động giải phóng khi ra khỏi phạm vi (scope).	Được thu gom tự động bởi Garbage Collector (GC).

Câu 2: Tính năng Init-only Properties (init) trong C# 9/10 khác gì so với thuộc tính
có set thông thường? Nêu trường hợp sử dụng thực tế.

Thuộc tính init cho phép thiết lập giá trị chỉ một lần duy nhất trong quá trình khởi tạo đối tượng.
•	Khác biệt với set thông thường:
o	Thuộc tính có set có thể thay đổi giá trị bất kỳ lúc nào trong suốt vòng đời đối tượng.
o	Thuộc tính có init chỉ cho phép gán giá trị tại hàm tạo (constructor) hoặc thông qua Object Initializer (cú pháp { Prop = value }). Sau đó, thuộc tính trở thành chỉ đọc (read-only).
•	Trường hợp sử dụng thực tế:
o	Dùng khi muốn tạo ra các đối tượng bất biến (Immutable Objects) (ví dụ: các lớp Data Transfer Object - DTO, các bản ghi cấu hình hệ thống cần đảm bảo không bị thay đổi dữ liệu sau khi tạo)


Câu 3: Phân biệt sự khác nhau giữa phương thức virtual ở lớp cha và phương
thức override ở lớp con khi triển khai tính Đa hình (Polymorphism).

Trong tính Đa hình (Polymorphism), virtual và override là bộ đôi từ khóa dùng để thiết lập cơ chế ghi đè phương thức:
•	Phương thức virtual (ở lớp cha):
o	Khai báo một phương thức có sẵn mã thực thi ở lớp cha nhưng cho phép các lớp con có thể định nghĩa lại nếu cần.
•	Phương thức override (ở lớp con):
o	Khai báo ở lớp con để chính thức ghi đè và thay thế hoàn toàn mã thực thi của phương thức virtual từ lớp cha.
•	Cơ chế hoạt động: Khi gọi phương thức qua một biến lớp cha nhưng trỏ đến đối tượng lớp con, chương trình sẽ gọi phiên bản override tại thời điểm chạy (Runtime).

Câu 4: Tại sao một thành phần được khai báo là static trong Lớp (Class) lại không thể
truy xuất thông qua một thể hiện (Object Instance) được tạo bằng toán tử new?

Từ khóa static định nghĩa các thành phần thuộc về chính bản thân Lớp (Class) chứ không thuộc về bất kỳ một thể hiện cụ thể nào.
•	Về mặt bộ nhớ: Thành phần static chỉ được cấp phát một vùng nhớ duy nhất cho toàn bộ ứng dụng ngay khi lớp được tải. Các đối tượng tạo bằng toán tử new nằm ở các vùng nhớ độc lập khác trên Heap và không sở hữu biến static đó.
•	Về mặt thiết kế ngôn ngữ: C# bắt buộc truy xuất qua tên lớp (ví dụ: ClassName.StaticMethod()) nhằm giúp mã nguồn rõ ràng, tránh gây hiểu lầm rằng thành phần đó có trạng thái riêng biệt thay đổi theo từng đối tượng.

