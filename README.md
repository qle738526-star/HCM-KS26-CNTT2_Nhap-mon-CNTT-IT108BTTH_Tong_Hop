# HCM-KS26-CNTT2_Nhap-mon-CNTT-IT108BTTH_Tong_Hop
## Stage4 
### Bài 1
**1. Sai lầm của Nam:**

Vị trí lưu: Lưu ở System32 gây lỗi hệ điều hành và mất dữ liệu.

Tên file: Có khoảng trắng gây lỗi gãy đường dẫn khi chạy code.

Mạng: 100 Mbps = 12.5 MB/s (vì 1 Byte = 8 bit).

**2. Cây thư mục (Ổ D, chuẩn kebab-case):**

Ổ cứng: Nhà sản xuất chia cho 1000, Windows chia cho 1024 nên 256GB thực tế chỉ hiển thị khoảng 238GB.
D:\ptit-workspace\
├─ 01-documents\
├─ 02-assignments\session-01\exercise-01.py
├─ 03-projects\mini-game\
└─ 04-archives\
### Bài 2
## 1. Phân Tích Kỹ Thuật và Luồng IPO

* **Nguyên nhân lỗi `FileNotFoundError`:** Do sử dụng đường dẫn tuyệt đối (`C:\Users\...`) gắn chặt với tên người dùng và cấu trúc ổ đĩa trên máy gốc. Khi chuyển sang máy khác, hệ điều hành không tìm thấy đường dẫn tương ứng nên báo lỗi.
* **Luồng xử lý IPO (Storage -> RAM):**
  * **Input:** Người dùng kích hoạt chạy tệp ứng dụng (`python main.py`).
  * **Process:** HĐH đọc tệp code và dữ liệu ảnh từ Storage (ổ cứng) nạp lên RAM; CPU truy xuất dữ liệu từ RAM để xử lý và dựng giao diện.
  * **Output:** Giao diện ứng dụng Shopee-Lite hiển thị logo và thông tin lên màn hình.
  * 
## 2. Giải Pháp Sửa Lỗi & Tối Ưu Hiệu Năng

* **Chuẩn hóa bằng đường dẫn tương đối (Relative Path):**
  * File code cùng cấp với `assets/`: `logo_path = "./assets/logo.png"` (`.` đại diện thư mục hiện tại).
  * File code nằm trong thư mục con: `logo_path = "../assets/logo.png"` (`..` đại diện thư mục cha).

* **3 bước xử lý giảm lag trên Task Manager (RAM 98%):**
  1.**Tắt ứng dụng chiếm RAM:** Mở Task Manager (Ctrl + Shift + Esc), lọc cột Memory và **End Task** các ứng dụng ngốn tài nguyên (Chrome, ứng dụng ngầm).
  2.**Giải phóng tiến trình bị treo:** Tắt trực tiếp tiến trình Python đang bị đơ để xả bộ nhớ tạm bị rò rỉ (memory leak).
  3.**Khởi động lại / Dọn bộ nhớ ảo:** Bật tính năng Memory Saver trên trình duyệt hoặc restart máy để Kernel dọn sạch tệp hoán đổi (Page File).
  ### BÀi 3
  ## 1. Môi Trường DIKW
* **Data (Dữ liệu):** Thu thập dữ liệu thô từ các cảm biến (nhiệt độ, độ ẩm)
* **Information (Thông tin):** Gửi thông báo tình trạng môi trường cho chủ vườn
* **Knowledge (Tri thức):** Tự động bật máy bơm khi nhiệt độ > 35°C
* **Wisdom (Trí tuệ):** Tối ưu lượng nước tưới dựa trên dự báo thời tiết

## 2. Xử Lý Bẫy Dữ Liệu & Tính Toán

* **Bật file ẩn (.env):** Bật **Hidden items** trong File Explorer để nhìn thấy và không xóa nhầm file .env chứa mật khẩu máy bơm.
* **Tính dung lượng ổ cứng (1 năm, dùng tối đa 70% đĩa):**
  * Dữ liệu 1 năm: 50 MB * 365 = 18,250 MB
  * Đổi sang GB: 18,250 / 1024 = 17.82 GB
  * Ổ cứng tối thiểu: 17.82 / 0.7 = 25.46 GB
  * **Kết luận:** Chọn thẻ nhớ/ổ cứng 32 GB
### BÀi 4
# Báo Cáo: Tối Ưu Hệ Thống Và Cây Thư Mục
## 1. Phân Tích và Chẩn Đoán
* **Chẩn đoán (Task Manager):** Mở 20 tab Chrome và VS Code làm tràn 8GB RAM.
* **RAM vs Storage:** RAM (Bàn làm việc) dùng xử lý tức thời; SSD (Ngăn tủ) dùng lưu trữ lâu dài.
* **Bẫy Swap File:** Khi RAM đầy, máy mượn tạm SSD làm bộ nhớ ảo. Việc luân chuyển dữ liệu liên tục làm quá tải SSD, gây giật lag.
* **Bẫy lưu trữ:** System32 là thư mục lõi. Lưu file ở đây dễ làm hỏng Windows và mất dữ liệu khi cài lại máy.


## 2. Thiết Kế Cây Thư Mục (Ổ D)
Dời dữ liệu sang ổ D: áp dụng quy tắc 3 cấp, 4 trụ cột và chuẩn kebab-case:

D:\ptit-workspace\
├─ 01-documents\python-guide.pdf

├─ 02-assignments\session-01\my-code.py

├─ 03-projects\python-first-project\main.py

└─ 04-archives\python-installer.exe
### Bài 5
## 1. Phân Tích & Tính Toán

### 1.1. Bảng so sánh đường dẫn
| Tiêu chí | Đường dẫn Tuyệt đối (Absolute) | Đường dẫn Tương đối (Relative) |
| :--- | :--- | :--- |
| **Đặc điểm** | Gắn cứng vào cấu trúc ổ đĩa của máy gốc (VD: `C:\Users\...`). | Dựa vào vị trí thư mục hiện tại đang chứa file code (dùng `.` hoặc `..`). |
| **Vấn đề** | Gây lỗi đứt gãy (File Not Found) khi chuyển dự án sang máy khác. | Đảm bảo tính di động (Portability), giữ liên kết chạy tốt trên mọi máy. |

### 1.2. Phép tính thời gian tải file 2GB với mạng 80 Mbps
* **Bước 1 (Đổi dung lượng file sang MB):** `2 GB = 2 * 1024 = 2048 MB` (vì 1 GB = 1024 MB).
* **Bước 2 (Đổi tốc độ mạng sang tốc độ tải thực tế):** `80 Mbps / 8 = 10 MB/s` .
* **Bước 3 (Tính thời gian tải):** `2048 / 10 = 204.8 giây` .

---

## 2. Hành Động Xử Lý

### 2.1. Sửa lại đường dẫn tương đối (Relative Path)
* **Đường dẫn chuẩn:** `./data/db.csv`  

### 2.2. Thiết lập nhận diện mã độc (View Options)
* **Thao tác:** Mở File Explorer ➔ Chọn thẻ **View** ➔ Tích chọn **File name extensions** (Hiển thị phần mở rộng của tệp).
* **Nhận diện:** Đuôi file thật sẽ hiện nguyên hình là `tai-lieu-on-tap.pdf.exe`. Nhờ thấy đuôi `.exe`, bạn biết ngay đây là phần mềm mã độc giả mạo tệp PDF để tránh click nhầm.
### Bài 6
## 1. Mô Hình DIKW & Luồng IPO
* **Data (Dữ liệu):** Lịch sử chi tiêu thô chưa qua xử lý. 
  *(IPO: Giao dịch mới ➔ Ghi nhận vào CSDL ➔ Tạo bản ghi 1KB)*.
* **Information (Thông tin):** Báo cáo tổng hợp chi tiêu hàng tháng theo từng danh mục. 
  *(IPO: Tập hợp dữ liệu thô ➔ Tính toán, gom nhóm ➔ Xuất Biểu đồ/Báo cáo)*.
* **Knowledge (Tri thức):** Cảnh báo khi người dùng có dấu hiệu chi tiêu vượt ngân sách. 
  *(IPO: Báo cáo tháng ➔ Đối chiếu với hạn mức ➔ Xuất thông báo cảnh báo)*.
* **Wisdom (Sự thông thái):** Gợi ý kế hoạch tiết kiệm và quản lý tài chính hiệu quả. 
  *(IPO: Thói quen chi tiêu ➔ Phân tích tài chính cá nhân ➔ Đưa ra gợi ý lộ trình)*.


## 2. Giải Quyết Ràng Buộc & Tính Toán
* **Bảo vệ file cấu hình ẩn (`.env`):** File `.env` chứa khóa bí mật API nhưng mặc định bị hệ điều hành ẩn.
   Cần bật tính năng **Hidden items** trong File Explorer để nhìn thấy chúng, giúp tránh việc vô tình xóa nhầm khi dọn dẹp dự án.
* **Tính dung lượng lưu trữ (1 ngày):**
  * Tổng dữ liệu phát sinh: `1 KB * 1,000,000 giao dịch = 1,000,000 KB`.
  * Quy đổi sang chuẩn MB: `1,000,000 / 1024 = 976.56 MB`.
  * **Kết luận:** Hệ thống cần khoảng **976.56 MB** không gian lưu trữ mỗi ngày.
  ## Stage 6
  ### Bài 1
  ## Phần 1: Phân Tích Lỗi Sai

* **Lỗi 1 (Sai cú pháp tạo và di chuyển thư mục chứa khoảng trắng):**
  * **Nguyên nhân:** Nam dùng lệnh `mkdir Smart Farm Project` và `cd Smart Farm Project` nhưng không bọc tên thư mục trong dấu ngoặc kép (`""`). Trong PowerShell, khoảng trắng được hiểu là dấu phân cách giữa các tham số độc lập. 
  * **Hậu quả:** Hệ thống hiểu lầm Nam đang tạo hoặc di chuyển giữa nhiều tham số rời rạc (`Smart`, `Farm`, `Project`) thay vì một thư mục thống nhất, dẫn đến lỗi cú pháp hoặc không tìm thấy đường dẫn.

* **Lỗi 2 (Sai quy ước ký tự phân cách đường dẫn trong PowerShell):**
  * **Nguyên nhân:** Nam sử dụng dấu xược xuôi `/` trong lệnh `mkdir src/sensors/temperature`. 
  * **Hậu quả:** Mặc dù PowerShell trên các phiên bản hiện đại có thể châm chước hiểu được, nhưng chuẩn thống kê và an toàn nhất trên hệ điều hành Windows PowerShell là sử dụng dấu xược ngược `\` (`src\sensors\temperature`).

## Phần 2: Hoàn Thiện (Chuỗi Lệnh Tối Ưu)

Để hoàn thành toàn bộ cấu trúc thư mục lồng nhau một cách chính xác và ít dòng lệnh nhất, Nam chỉ cần sử dụng **1 dòng lệnh PowerShell** duy nhất sau:

mkdir "Smart Farm Project\src\sensors\temperature"
### Bài 2
# 1. Mục Tiêu & Bối Cảnh
* **Mục tiêu:** Thực hành các lệnh tạo thư mục và tạo file bằng Terminal (`mkdir`, `touch`/`New-Item`).
* **Bối cảnh:** Hệ thống **OrderTech** đang được cập nhật module `Quản lý Đồ Uống` từ thư mục gốc `/home/OrderTech/`.



# 2. Hoàn Thiện Kịch Bản Terminal

* Bước 1: Tạo thư mục drink_module
mkdir drink_module

* Bước 2: Di chuyển vào thư mục vừa tạo
cd drink_module

* Bước 3: Tạo đồng thời 2 file trống coffee.txt và tea.txt
touch coffee.txt tea.txt
### Bài 3
## 1. Sơ Đồ Luồng IPO
* **Input:** Yêu cầu tạo thư mục `smart-farm\data\logs`, `smart-farm\code`, 3 file (`config.json`, `sensors.py`, `.env`) và sao lưu code.
* **Process:** Thực thi câu lệnh PowerShell tạo đệ quy và sao chép.
* **Output:** Hạ tầng thư mục, file cấu hình và thư mục backup hoàn chỉnh.

## 2. Câu Lệnh PowerShell
* **Tạo thư mục lồng nhau:**

  New-Item -ItemType Directory -Force -Path "smart-farm\data\logs", "smart-farm\code"

* **Tạo đồng thời 3 file:**

*New-Item -ItemType File -Force -Path "smart-farm\code\config.json", "smart-farm\code\sensors.py"

* **Sao chép thư mục đệ quy:**

*Copy-Item -Path "smart-farm\code" -Destination "smart-farm\backup\code_v1" -Recurse
### Bài 4
## Phần 1: Bảng So Sánh Hai Giải Pháp

| Tiêu Chí | Đường Dẫn Tuyệt Đối (Absolute Path)<br>`C:\Users\An-K26\FarmProject\data\logs.csv` | Đường Dẫn Tương Đối (Relative Path)<br>`../data/logs.csv` |
| :--- | :--- | :--- |
| **Độ dài & Cấu trúc** | Dài, gắn cứng toàn bộ cây thư mục từ gốc ổ đĩa `C:\`. | Ngắn gọn, định vị dựa vào vị trí thư mục hiện tại. |
| **Tính di động (Portability)** | **Kém:** Gây lỗi `FileNotFoundError` ngay lập tức nếu đổi tên máy, đổi tên User (`An-K26`), hoặc đổi ổ đĩa. | **Cao:** Dự án chạy mượt mà trên mọi máy tính và mọi hệ điều hành khi gửi cho người khác. |


## Phần 2: Lựa Chọn Giải Pháp Tối Ưu Và Ý Nghĩa Ký Hiệu

* **Lựa chọn tối ưu:** Sử dụng **Relative Path (`../data/logs.csv`)**.
* **Ý nghĩa ký hiệu `..`:** Ký hiệu này đại diện cho **thư mục cha (Parent Directory)** — tức là lùi lại một cấp thư mục so với vị trí file script hiện tại để tìm đến thư mục `data` và đọc file `logs.csv`. Đây là tiêu chuẩn chuyên nghiệp giúp mã nguồn có tính di động tuyệt đối.
### Bài 5
## 1. Sơ Đồ Luồng IPO
* **Input:** Thư mục `Downloads` chứa hỗn hợp file (`.png`, `.jpg`, `.py`, `.tmp`).
* **Process:** Kiểm tra định dạng, phân loại file, xử lý ngoại lệ tránh lỗi "Is a directory", sau đó di chuyển và xóa file tạm.
* **Output:** Thư mục gọn gàng: ảnh nằm trong `media/`, code nằm trong `scripts/`, file `.tmp` đã bị xóa.

## 2. Câu Lệnh Kịch Bản (Bash / Linux)
* **Khởi tạo thư mục đích:**

  mkdir -p media scripts
 * **Gom file ảnh và code (có kiểm tra an toàn):**

[ -d media ] && mv *.png *.jpg media/ 2>/dev/null
[ -d scripts ] && mv *.py scripts/ 2>/dev/null

* **Xóa file tạm giải phóng dung lượng:**

rm -f *.tmp
### Bài 6
## 1. Bản Phân Tích Luồng IPO
* **Input:** Yêu cầu thiết lập từ thư mục Home (`~`), tạo thư mục, file ẩn, sao chép file mẫu và kiểm tra.
* **Process:** Dùng `New-Item`, `Copy-Item`, tham số `-Force` để hiện file ẩn, và nâng quyền Administrator khi gặp lỗi truy cập.
* **Output:** Cấu trúc thư mục `smart-farm` hoàn chỉnh, bảo mật và sẵn sàng vận hành.

## 2. Nhật Ký Lệnh PowerShell
* **Tạo thư mục gốc và thư mục con:**

  New-Item -ItemType Directory -Force -Path "~\smart-farm\bin", "~\smart-farm\config", "~\smart-farm\data"

* **Tạo file ẩn .env:**

New-Item -ItemType File -Force -Path "~\smart-farm\config\.env"

* **Sao chép và đổi tên file từ Public:**

Copy-Item -Path "C:\Users\Public\template.ps1" -Destination "~\smart-farm\bin\pump_control.ps1"

* **Kiểm tra toàn bộ cấu trúc:**
## Stage 8
### Bài 1
# Bài 1: Xử lý Log máy chủ dung lượng lớn (800MB)

## Phần 1: Phân tích nguyên nhân lỗi

*   **Vì sao Notepad bị "Not Responding"?**
    Notepad hoạt động theo cơ chế nạp toàn bộ dữ liệu của tệp vào RAM cùng một lúc. Mở tệp 800MB sẽ ngốn ngay lập tức hàng trăm MB RAM, vượt quá khả năng xử lý của trình soạn thảo văn bản đơn giản này, dẫn đến tràn bộ nhớ và treo máy (Not Responding).
*   **Vì sao lệnh `cat` báo lỗi trong CMD?**
    `cat` vốn là một lệnh đặc trưng của hệ điều hành Unix/Linux (hoặc Bash shell). Trình thông dịch dòng lệnh cũ của Windows (CMD/Command Prompt) không hỗ trợ lệnh này, nên nó báo "command not found".
*   **Vì sao `cat` lại hoạt động được trên PowerShell?**
    PowerShell hỗ trợ tính năng **Alias (bí danh)**. Lệnh `cat` trong PowerShell thực chất được gán làm bí danh cho lệnh gốc `Get-Content`. Do đó, người dùng quen thuộc với Linux có thể gõ `cat` trên PowerShell và hệ thống vẫn hiểu đó là lệnh đọc tệp.

## Phần 2: Giải pháp (Bộ lệnh chuẩn trên PowerShell)

Để xử lý tệp log 800MB một cách mượt mà bằng luồng (stream) mà không làm treo máy, hãy sử dụng các lệnh sau:

1.  **Xem toàn bộ nội dung tệp:**
    Get-Content server_log_800MB.log
2.  **Chỉ xem 10 dòng cuối cùng (để kiểm tra lỗi mới nhất):**
    Get-Content server_log_800MB.log -Tail 10
### Bài 2
# Bài 2: Phân biệt bản chất Tìm vị trí tệp vs Tìm nội dung

## Phần 1: Phân tích sự nhầm lẫn của An

*   **Tư duy sai lệch:** An đang nhầm lẫn giữa việc "tìm tên tệp" và "tìm nội dung bên trong tệp". Lệnh `Get-ChildItem -Recurse -Filter "*404*"` mà An dùng chỉ yêu cầu hệ điều hành tìm các tệp/thư mục có **tên** chứa chuỗi "404" (ví dụ: `error404.log`), chứ hoàn toàn không đọc vào dữ liệu bên trong tệp `access.log`.
*   **Sự khác biệt cốt lõi:**
    *   **`Get-ChildItem`**: Dùng để định vị, duyệt cây thư mục và liệt kê danh sách các tệp tin/thư mục (Metadata).
    *   **`Select-String`**: Dùng để quét, đọc và tìm kiếm các chuỗi ký tự nằm sâu *bên trong* nội dung của tệp (Content).

## Phần 2: Giải pháp (Bộ lệnh chuẩn trên PowerShell)

Để lọc từ khóa "error" bên trong tệp `access.log`, ta kết hợp lệnh đọc tệp và lệnh lọc chuỗi:


Get-Content access.log | Select-String "error"
### Bài 3 Kỹ thuật Pipeline trong PowerShell 

## 1. Bản chất Pipeline
*   **PowerShell:** Truyền **đối tượng (Object)**. Có thể đếm nhanh bằng thuộc tính `.Count`.
*   **Bash/CMD:** Truyền văn bản thô (Text), phải dùng lệnh đếm riêng (như `wc -l`).

## 2. Lệnh đếm TIMEOUT (loại trừ "NOT TIMEOUT")

(Get-Content server.log | Select-String "TIMEOUT" | Where-Object { $_ -notmatch "NOT TIMEOUT" }).Count

**Giải thích:**
Dấu `()` bọc toàn bộ quy trình đọc và lọc, sau đó gọi trực tiếp `.Count` từ mảng đối tượng trả về để xuất ra một con số duy nhất.
### Bài 4
## 1. So sánh `>` và `>>`

| Tiêu chí | `>` (Ghi đè - Overwrite) | `>>` (Ghi nối - Append) |
| :--- | :--- | :--- |
| **Cơ chế** | Xóa sạch toàn bộ nội dung cũ, ghi đè dữ liệu mới. | Thêm dữ liệu mới vào dòng cuối cùng của tệp. |
| **Rủi ro (Bẫy)** | **Rất cao:** Nếu gõ nhầm vào cuối tháng, toàn bộ báo cáo tích lũy 30 ngày sẽ bị xóa sạch không thể khôi phục. | **An toàn:** Giữ nguyên dữ liệu lịch sử, không gây mất mát. |
| **Ngữ cảnh** | Tạo báo cáo mới (Khởi tạo ca sáng). | Theo dõi log phát sinh liên tục (Giám sát 24/7). |
| **Encoding** | Alias của lệnh `Out-File` (Mặc định UTF-16). | Alias của lệnh `Out-File -Append` (Mặc định UTF-16). |

## 2. Giải pháp tối ưu cho ghi nhật ký liên tục

*   **Lựa chọn chốt:** Bắt buộc dùng cơ chế **ghi nối tiếp** để đảm bảo tính toàn vẹn của nhật ký hệ thống phát sinh trong ngày.
*   **Tối ưu Encoding:** Vì `>>` mặc định xuất ra tệp UTF-16 (có thể gây lỗi hiển thị ký tự trên một số công cụ đọc), giải pháp tốt nhất là sử dụng rõ ràng lệnh `Add-Content` hoặc `Out-File -Append` kết hợp cờ ép kiểu mã hóa UTF-8.

**Lệnh đề xuất:**
### Bài 5 Đóng gói quy trình tự động bằng PowerShell Script (.ps1)

## Phần 1: Thiết kế kiến trúc 4 khối

1.  **Header block:** Ghi chú thông tin metadata của script (tên, tác giả, ngày tháng) bằng dấu `#`.
2.  **Biến cấu hình:** Đặt đường dẫn file log và file báo cáo vào các biến `$log_file`, `$report_file` để dễ dàng tái sử dụng và chỉnh sửa.
3.  **Thông báo tiến trình:** Sử dụng `Write-Host` để in trạng thái ra màn hình console (không bị ghi nhầm vào file báo cáo).
4.  **Logic xử lý:** Đọc file, lọc bằng Pipe `|` và lưu kết quả bằng toán tử chuyển hướng `> / >>`.

## Phần 2: Sản phẩm (Mã nguồn `auto_report.ps1`)

Tạo file `auto_report.ps1` và dán đoạn mã sau vào:

# 1. Header block
# Ten script: auto_report.ps1
# Tac gia: Le Quoc Minh Quan
# Chuc nang: Tu dong loc loi 404 tu file log va xuat bao cao

# 2. Bien cau hinh
$log_file = "server.log"
$report_file = "report.txt"

# 3. Thong bao tien trinh
### Bài 6
## Phần 1: Phân tích (Auditing)

*   **Điểm cực kỳ nguy hiểm:** Dòng lệnh `Remove-Item -Path "C:\*" -Recurse -Force`.
*   **Giải thích tham số:**
    *   `-Path "C:\*"`: Chỉ định mục tiêu xóa là toàn bộ dữ liệu ở thư mục gốc của ổ đĩa C.
    *   `-Recurse`: Thực hiện xóa đệ quy, quét và xóa sạch mọi thư mục con và tệp tin sâu bên trong.
    *   `-Force`: Ép buộc xóa bỏ qua các cảnh báo bảo mật, can thiệp xóa cả tệp ẩn hay tệp hệ thống (System files).
*   **Hậu quả:** Xóa sạch toàn bộ hệ điều hành Windows, phần mềm và dữ liệu người dùng. Hệ thống sẽ lập tức tê liệt, sập hoàn toàn và gây mất dữ liệu nghiêm trọng.
*   **Áp dụng 3 Nguyên tắc "Vàng" thẩm định mã AI:**
    1.  **Hiểu rõ trước khi chạy:** Phải giải nghĩa được mọi lệnh (`Remove-Item`) và toàn bộ tham số do AI tạo ra.
    2.  **Khoanh vùng Đường dẫn:** Tuyệt đối không dùng đường dẫn hệ thống/ổ đĩa (`C:\*`). Luôn dùng đường dẫn tương đối (ví dụ `.\`) để giới hạn tác động chỉ trong thư mục dự án hiện tại.
    3.  **Kiểm tra từng bước (Test/Verify):** Chạy thử script trên một thư mục nháp (ảo) trước khi cho phép chạy trên máy chủ thật.

## Phần 2: Triển khai (Safe Script)

Tạo tệp `safe_cleanup.ps1` tuân thủ nghiêm ngặt nguyên tắc "Khoanh vùng Đường dẫn":

# 1. Di chuyen den thu muc logs (Gia su ban dang dung o thu muc goc cua du an)
Set-Location ".\logs"

# 2. Loc cac dong WARNING ra tep issues.txt (Dung > de tao moi/ghi de bao cao)
## Stage 10
### Bài 1
## Phần 1: Phân tích các lỗi cú pháp

Đoạn mã của sinh viên mắc 3 lỗi cơ bản sau khiến kết quả render bị lộn xộn:

1.  **Lỗi phân cấp tiêu đề (Heading):** Nhảy bậc từ H1 (`#`) xuống thẳng H3 (`###`). Theo chuẩn, tiêu đề phải giảm dần theo thứ bậc logic (H1 -> H2 -> H3) để tạo cấu trúc rõ ràng. H1 cũng chỉ nên xuất hiện 1 lần đại diện cho tên bài viết.
2.  **Lỗi cú pháp chèn ảnh (Image):** Đoạn `[Logo Dự án] (https://greentech.vn/logo.png)` bị thiếu dấu chấm than `!` ở đầu và bị thừa một khoảng trắng giữa dấu `]` và `(`. Vì vậy, trình biên dịch (như StackEdit) sẽ hiểu nhầm đây là một siêu liên kết (Link) bị viết sai cú pháp thay vì hiển thị hình ảnh.
3.  **Lỗi cú pháp in đậm (Emphasis):** Việc chỉ dùng 1 dấu sao (ví dụ: `*Rất quan trọng*`) sẽ làm chữ bị **in nghiêng (Italic)**. Để in đậm (Bold), bắt buộc phải dùng 2 dấu sao bọc quanh từ khóa.

## Phần 2: Đoạn mã hoàn thiện (Corrected Code)

Dưới đây là đoạn mã chuẩn đã sửa lỗi, đảm bảo hiển thị đúng ảnh logo, cấu trúc tiêu đề hợp lý (H1 -> H2) và chữ in đậm:

![Logo Dự án](https://greentech.vn/logo.png)

# Lợi ích của rau sạch
### Bài 2
## Phần 1: Phân tích (I/O)
*   **Input:** Văn bản thô nhập từ bàn phím (chữ thuần túy).
*   **Output:** Giao diện trực quan (code được tô màu, bảng biểu chia cột ngay ngắn, danh sách có ô tick chọn).

## Phần 2: Mã nguồn Markdown (Source Code)

Dưới đây là nội dung file `.md` đáp ứng đủ yêu cầu:

# Hướng dẫn cài đặt cảm biến

\* Lưu ý: Cẩn thận không làm chập chân \#5.

## 1. So sánh thiết bị

| Tiêu chí | Cảm biến cũ | Cảm biến mới |
| :--- | :--- | :--- |
| **Độ chính xác** | Thấp | Cao |

## 2. Chuẩn bị (Task List)

## 2. Chuẩn bị (Task List)

- [x] Tắt nguồn điện.
- [ ] Mở Terminal, chạy lệnh `pip install adafruit-dht` để cài thư viện.

## 3. Code điều khiển máy bơm

```python
humidity = 55.0
if humidity < 60.0:
    print("Độ ẩm thấp -> Bật máy bơm!")
else:
    print("Độ ẩm ổn định.")
```
### Bài 3
## Phần 1: Phân tích bài toán (Cơ chế Token)
*   **HTML:** Sử dụng hệ thống thẻ đóng/mở phức tạp (ví dụ: `<strong>...</strong>`). Điều này làm lãng phí lượng lớn Token của AI chỉ để xử lý các ký tự định dạng, làm giảm tốc độ sinh văn bản.
*   **Markdown:** Sử dụng các ký tự đặc biệt tối giản (ví dụ: `**...**`). Giúp tối ưu hóa số lượng Token, AI xử lý nhanh hơn (giảm độ trễ) và tiết kiệm trực tiếp chi phí API.

## Phần 2: So sánh Và Đánh giá

| Tiêu chí | Markdown | HTML |
| :--- | :--- | :--- |
| **Cú pháp in đậm** | `**Rau sạch**` | `<strong>Rau sạch</strong>` |
| **Tính Human-readable** | Rất cao (Đọc tốt ngay cả khi là văn bản thô) | Thấp (Rối mắt bởi các thẻ định dạng) |
| **Chi phí Token** | Thấp (Tối ưu) | Cao (Lãng phí) |
| **Tốc độ AI xử lý** | Nhanh | Chậm |

### Giải pháp tối ưu cho hệ thống "GreenTech"

**Lựa chọn chốt:** Sử dụng định dạng **Markdown**.
**Lập luận:**
1.  **Hiệu năng & Kinh tế:** Tiết kiệm lượng Token phát sinh, giúp hệ thống phản hồi các câu hỏi nông nghiệp nhanh chóng và giảm chi phí vận hành API.
2.  **Trải nghiệm người dùng (UX):** Markdown mang tính "Human-readable" cao. Trong trường hợp xấu nhất hệ thống lỗi không hiển thị được giao diện, người nông dân nhìn vào văn bản Markdown thô vẫn hoàn toàn có thể đọc hiểu thông tin, trong khi HTML sẽ hiển thị một mớ thẻ code `<br>`, `<li>` gây khó hiểu.
### Bài 4
## Phần 1: Mẫu Prompt (Đầu vào)

# Đóng vai
Gia sư IT.

## Bối cảnh
Sinh viên năm 1 cần hiểu "Mô hình IPO".

## Nội dung
Giải thích mô hình IPO qua ví dụ hệ thống tưới vườn Lan.

## Yêu cầu
- [x] Lập bảng tóm tắt Input, Processing, Output.
- [x] Dùng ngôn ngữ đơn giản, dễ hiểu.

## Không cần
Không viết code, không dùng thuật ngữ chuyên sâu.

## Phần 2: Kết quả AI trả về (Đầu ra)

# Mô hình IPO: Hệ thống tưới Lan

| Pha | Chức năng | Ví dụ thực tế |
| :--- | :--- | :--- |
| **Input** | Nhận dữ liệu | Cảm biến báo độ ẩm đất đang là 40% (khô). |
| **Processing**| Xử lý phân tích | Máy tính so sánh: 40% < 60% ➔ Quyết định tưới. |
| **Output** | Hành động | Bật máy bơm phun sương. |
### Bài 5
# Dự án Smart-Farm
Hệ thống tự động chăm sóc hoa Lan.

## 1. Tính năng chính
- Đo nhiệt độ/độ ẩm.
- Tự động tưới nước.
- Gửi tin nhắn cảnh báo.

## 2. Cấu trúc thiết bị (Mô hình IPO)
- **Đầu vào (Input):** Cảm biến đo dữ liệu môi trường.
- **Xử lý (Processing):** Mạch Raspberry Pi tính toán dữ liệu.
- **Đầu ra (Output):** Máy bơm phun nước.

## 3. Cách chạy
Tải mã nguồn về máy và gõ lệnh chạy file python.

## 4. Nguyên lý hoạt động
- **Hoạt động của chip (CPU):** Lấy lệnh -> Dịch hiểu lệnh -> Cấp điện cho máy bơm chạy.
- **Logic ra quyết định (DIKW):** Đọc được số liệu -> Hiểu là 36 độ C và đất rất khô -> Nhận định cây đang thiếu nước -> Quyết định bật máy bơm ngay lập tức.

## 5. Lưu ý bảo trì
Máy chạy lâu sẽ lưu nhiều file nhật ký (log) gây đầy RAM và treo máy. Chỉ cần vào đúng thư mục chứa log để xóa các file cũ là được, tuyệt đối không gõ lệnh xóa sạch toàn bộ ổ đĩa.
### Bài 6
## Phần 1. Phân tích sai lầm của Nam

Nam mắc 2 sai lầm chính khi dùng file Word (.docx) đẩy lên GitHub:
1. **Gây lỗi xung đột (Conflict) trên Git:** File Word là dạng **Rich Text** (thực chất là file nén mã hóa phức tạp). Khi sửa dù chỉ 1 dấu phẩy, toàn bộ cấu trúc file bị biến đổi. Git (vốn thiết kế để theo dõi từng dòng văn bản thô) sẽ không hiểu được thay đổi này và báo lỗi toàn bộ file.
2. **Không đọc được trực tiếp:** GitHub và các trình duyệt không thể hiển thị ngay nội dung file `.docx`. Thành viên nhóm phải tải file về và dùng phần mềm chuyên dụng (Microsoft Word) mới mở được.

**Sự an toàn và ưu việt của Markdown:**
- **Chống hỏng file (Corrupt):** File Word rất dễ tổn thương; chỉ cần rớt mạng làm mất 1 byte dữ liệu, toàn bộ file sẽ bị hỏng và không thể mở được. Ngược lại, Markdown là **Plain Text** (văn bản thô). Nếu mất 1 byte, tài liệu chỉ bị mất đúng 1 ký tự đó, các phần còn lại vẫn an toàn và đọc bình thường.
- **Tương thích hoàn hảo:** Markdown rất nhẹ, hiển thị trực tiếp đẹp mắt trên web và giúp Git dễ dàng theo dõi từng dòng bị chỉnh sửa.

## Phần 2. Hoàn thiện (Chuyển đổi sang Markdown)

Dưới đây là mẫu tài liệu giới thiệu dự án đã được chuyển đổi sang định dạng Markdown (tối ưu cho StackEdit và GitHub):

# Giới thiệu dự án GreenTech

Dự án **GreenTech** nhằm ứng dụng công nghệ IoT để xây dựng hệ thống nông nghiệp thông minh.

## Chức năng chính
- Theo dõi nhiệt độ và độ ẩm liên tục.
- Hệ thống bơm nước hoạt động tự động.
- Xuất báo cáo nhật ký hệ thống (Log).



