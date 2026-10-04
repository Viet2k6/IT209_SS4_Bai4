# Bài 4: Quản lý tệp tin bỏ qua (.gitignore) và Sửa lịch sử (Amend)

## 1. Mục tiêu

Thực hành cấu hình `.gitignore`, gỡ file đã commit khỏi Git bằng `git rm --cached` và sửa commit gần nhất bằng `git commit --amend`.

## 2. Các bước thực hiện

### Bước 1: Commit nhầm file credentials.txt

Tạo file `credentials.txt` và commit vào Git:

```bash
echo "username=admin" > credentials.txt
git add credentials.txt
git commit -m "Add credentials file"
```

### Bước 2: Cấu hình .gitignore

Tạo file `.gitignore`:

```bash
echo "credentials.txt" > .gitignore
```

Nội dung `.gitignore`:

```text
credentials.txt
```

### Bước 3: Gỡ credentials.txt khỏi Git

Sử dụng:

```bash
git rm --cached credentials.txt
```

Lệnh này chỉ gỡ file khỏi vùng theo dõi của Git, không xóa file vật lý trên máy.

### Bước 4: Commit và sử dụng --amend

```bash
git add .gitignore
git commit -m "Ignore credentials file"
git commit --amend -m "Remove credentials and update gitignore"
```

## 3. Kiểm tra

Kiểm tra file vẫn tồn tại:

```bash
ls -l credentials.txt
```

Kết quả: `credentials.txt` vẫn tồn tại trong thư mục làm việc.

Kiểm tra trạng thái Git:

```bash
git status
```

Kết quả:

```text
On branch master
nothing to commit, working tree clean
```

Kiểm tra commit gần nhất:

```bash
git log -n 1
```

Commit gần nhất có thông điệp:

```text
Remove credentials and update gitignore
```

## 4. Kết quả

* `credentials.txt` vẫn được giữ lại trên máy.
* `credentials.txt` không còn được Git theo dõi.
* `.gitignore` được cấu hình để bỏ qua `credentials.txt` trong tương lai.
* Sử dụng thành công `git rm --cached`.
* Sử dụng thành công `git commit --amend` để sửa commit gần nhất.
