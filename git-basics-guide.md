# 🎓 Git Cơ Bản - Hướng Dẫn Toàn Diện

## 📚 Mục Lục
1. [Commit Là Gì?](#commit-là-gì)
2. [Branch Là Gì?](#branch-là-gì)
3. [HEAD Là Gì?](#head-là-gì)
4. [Local vs Remote](#local-vs-remote)
5. [Ví Dụ Thực Tế Của Bạn](#ví-dụ-thực-tế-của-bạn)

---

## 🎯 Commit Là Gì?

### Định Nghĩa Đơn Giản:
**Commit = 1 Bức Ảnh Chụp** (snapshot) của toàn bộ code tại 1 thời điểm

### Ví Dụ Dễ Hiểu:
Giống như chơi game có **Save Point** 🎮
- Save 1: Có file A.md
- Save 2: Có file A.md + B.md  
- Save 3: Có file A.md + B.md + C.md

```
Commit 3: 📸 [A.md + B.md + C.md]  ← Mới nhất
   ↑
Commit 2: 📸 [A.md + B.md]
   ↑
Commit 1: 📸 [A.md]  ← Đầu tiên
```

### Mỗi Commit Có:
- **Hash** (Mã số): `a09f5a2` (7 ký tự) hoặc `a09f5a27ba5e7...` (đầy đủ)
- **Message**: "Add A.md file for learning GitHub"
- **Tác giả**: Ho Thi Ngoc Le
- **Thời gian**: Mon Feb 9 21:06:48 2026
- **Parent** (Cha): Commit trước đó (nếu có)

### Loại Commit:
| Loại | Số Parent | Ví Dụ |
|------|-----------|-------|
| **Root commit** | 0 (không có cha) | Commit đầu tiên |
| **Regular commit** | 1 (1 cha) | Commit thường |
| **Merge commit** | 2+ (nhiều cha) | Khi merge branch |

---

## 🌳 Branch Là Gì?

### Định Nghĩa Đơn Giản:
**Branch = Nhãn Dán** (label) trỏ đến 1 commit

### Ví Dụ Dễ Hiểu:
Tưởng tượng có 3 quyển sách:
```
Sách "main"       → Trang 100 (commit ac1550a)
Sách "abc-branch" → Trang 150 (commit 0fad6e2)
```

**Branch chỉ là cái tên** - nội dung thật sự nằm ở **commit**!

### Các Loại Branch:

#### 1️⃣ **Local Branch** (Trên Máy Bạn)
```
main         ← Branch trên máy bạn
abc-branch   ← Branch trên máy bạn
```

#### 2️⃣ **Remote Branch** (Trên GitHub)
```
origin/main      ← Bản sao từ GitHub
origin/HEAD      ← Con trỏ mặc định (trỏ sang origin/main)
```

### Tại Sao Cần Branch?
- ✅ Làm việc song song (feature mới, sửa bug)
- ✅ Không làm hỏng code chính (main)
- ✅ Dễ quay lại khi sai

---

## 👉 HEAD Là Gì?

### Định Nghĩa Đơn Giản:
**HEAD = Ngón Tay Bạn** 👆 đang trỏ vào đâu

### 2 Trạng Thái:

#### ✅ **Attached HEAD** (Bình Thường)
```
HEAD → main → commit ac1550a
```
Ngón tay trỏ vào **branch**, branch trỏ vào **commit**

**Ví dụ:**
```
YOU 👆
  ↓
main (branch)
  ↓
● Commit ac1550a
```

#### ⚠️ **Detached HEAD** (Nguy Hiểm)
```
HEAD → commit 0fad6e2 (trực tiếp, không qua branch)
```
Ngón tay trỏ **trực tiếp** vào commit, bỏ qua branch

**Ví dụ:**
```
YOU 👆
  ↓
● Commit 0fad6e2 (không có branch)
```

### Tại Sao Detached HEAD Nguy Hiểm?
Nếu tạo commit mới rồi chuyển đi → **commit mới sẽ mất!**

**Cách khắc phục:**
```bash
git branch new-branch-name  # Tạo branch để lưu
```

---

## 🌍 Local vs Remote

### Định Nghĩa:

| | Local | Remote |
|---|---|---|
| **Vị trí** | Máy tính của bạn 💻 | GitHub (internet) ☁️ |
| **Branch** | `main`, `abc-branch` | `origin/main` |
| **Truy cập** | Chỉ bạn | Mọi người (nếu public) |

### Quy Trình:

```
MÁY BẠN                    GITHUB
(Local)                    (Remote)

main ──────push──────→ origin/main
     ←─────pull───────
```

### Lệnh Quan Trọng:
```bash
git push    # Đẩy code từ local → remote (GitHub)
git pull    # Kéo code từ remote → local
git fetch   # Xem có gì mới trên remote (không merge)
```

### Tên `origin` Là Gì?
**origin = Tên Nickname** của GitHub repository

Khi bạn `git clone`, Git tự đặt tên remote là `origin`

```bash
origin = https://github.com/binhphuong-ab/Learn-Github
```

---

## 🎯 Ví Dụ Thực Tế Của Bạn

### 📊 Cấu Trúc Repository:

```
* 0fad6e2 (HEAD, abc-branch) Add C.md file - now have A, B, and C
* 43f3977 Add B.md file at earlier commit position
| * ac1550a (origin/main, origin/HEAD, main) Add GitHub Keychain authentication
|/  
* a09f5a2 Add A.md file for learning GitHub
```

### 🔍 Giải Thích Từng Phần:

#### **Commit a09f5a2** (Root commit)
```
✅ Commit đầu tiên
✅ Có file: A.md
✅ Trên branch: main, abc-branch (cả 2)
✅ Đã push lên GitHub
```

#### **Nhánh Rẽ** (Fork)
Từ `a09f5a2`, có **2 đường đi**:

**Đường 1 (main):**
```
a09f5a2 → ac1550a (main)
```

**Đường 2 (abc-branch):**
```
a09f5a2 → 43f3977 → 0fad6e2 (abc-branch)
```

#### **Commit ac1550a**
```
✅ Trên branch: main
✅ Đã push lên GitHub (origin/main)
✅ Có file: A.md + github-key-chain.md
```

#### **Commit 43f3977**
```
✅ Trên branch: abc-branch
❌ Chưa push lên GitHub
✅ Có file: A.md + B.md
```

#### **Commit 0fad6e2**
```
✅ Trên branch: abc-branch
✅ HEAD đang ở đây
❌ Chưa push lên GitHub
✅ Có file: A.md + B.md + C.md
```

### 🏷️ Các Branch:

| Branch | Trỏ Đến Commit | Ở Đâu? | File Hiện Có |
|--------|----------------|--------|--------------|
| `main` | `ac1550a` | Local + GitHub | A.md, github-key-chain.md |
| `abc-branch` | `0fad6e2` | Local only | A.md, B.md, C.md |
| `origin/main` | `ac1550a` | GitHub | A.md, github-key-chain.md |

### 👆 HEAD Hiện Tại:
```
HEAD → 0fad6e2 (detached!)
```
**Vấn đề:** Đang ở detached HEAD (không an toàn)

**Giải pháp:** Đã tạo branch `abc-branch` để lưu → An toàn rồi! ✅

---

## 🎓 Tóm Tắt Các Khái Niệm

| Khái Niệm | Tiếng Anh | So Sánh |
|-----------|-----------|---------|
| Commit | Commit | Bức ảnh chụp code 📸 |
| Branch | Branch | Nhãn dán/bookmark 🏷️ |
| HEAD | HEAD | Ngón tay trỏ 👆 |
| Local | Local | Máy bạn 💻 |
| Remote | Remote | GitHub ☁️ |
| Attached HEAD | On a branch | Trỏ qua branch (an toàn) ✅ |
| Detached HEAD | Detached | Trỏ trực tiếp commit (nguy hiểm) ⚠️ |
| Root commit | Initial commit | Commit đầu tiên 🌱 |

---

## 💡 Các Lệnh Cơ Bản

### Xem Commit:
```bash
git log -3                    # 3 commit gần nhất
git log --oneline             # Gọn gàng 1 dòng
git log --graph --all         # Xem dạng cây
git show HEAD                 # Xem commit hiện tại
git show a09f5a2              # Xem commit cụ thể
```

### Xem Branch:
```bash
git branch                    # Branch local
git branch -a                 # Tất cả branch (local + remote)
git branch -r                 # Chỉ remote branch
```

### Di Chuyển:
```bash
git checkout main             # Chuyển sang branch main
git checkout abc-branch       # Chuyển sang branch abc-branch
git checkout a09f5a2          # Chuyển đến commit (detached!)
```

### Tạo Branch:
```bash
git branch new-branch         # Tạo branch mới
git checkout -b new-branch    # Tạo + chuyển luôn
```

### Push/Pull:
```bash
git push origin main          # Đẩy main lên GitHub
git pull origin main          # Kéo main từ GitHub
git fetch                     # Xem có gì mới
```

---

## ❓ Câu Hỏi Thường Gặp

### 1. **Tại sao có `origin/main` và `main`?**
- `main` = Branch trên máy bạn
- `origin/main` = Bản sao từ GitHub (lần cuối fetch/pull)

### 2. **Làm sao biết đang ở branch nào?**
```bash
git status                    # Cách 1
git branch                    # Cách 2 (có dấu *)
```

### 3. **Detached HEAD có nguy hiểm không?**
Nếu CHỈ XEM thì không sao. Nhưng nếu commit mới thì nguy hiểm!

### 4. **Làm sao để push `abc-branch` lên GitHub?**
```bash
git checkout abc-branch
git push origin abc-branch
```

### 5. **Có thể xóa commit không?**
Có, nhưng cẩn thận! Dùng `git reset` hoặc `git revert`

---

## 🎯 Thực Hành Với Repository Của Bạn

### Để xem 3 commits (A, B, C):
```bash
# Cách 1: Ở vị trí HEAD
git log -3 --oneline

# Cách 2: Chỉ định commit
git log -3 --oneline 0fad6e2

# Cách 3: Xem từ branch
git log --oneline abc-branch
```

### Để chuyển sang branch an toàn:
```bash
git checkout abc-branch      # Attached HEAD
git checkout main            # Về main
```

### Để push abc-branch lên GitHub:
```bash
git checkout abc-branch
git push origin abc-branch
```

---

## 🎉 Kết Luận

**Git không khó, chỉ cần nhớ:**

1. **Commit** = Ảnh chụp code 📸
2. **Branch** = Nhãn dán 🏷️
3. **HEAD** = Bạn đang ở đâu 👆
4. **Local** = Máy bạn 💻
5. **Remote** = GitHub ☁️

**Quy tắc vàng:**
- ✅ Luôn tạo branch cho tính năng mới
- ✅ Commit thường xuyên với message rõ ràng
- ✅ Push lên GitHub để backup
- ⚠️ Tránh detached HEAD khi làm việc

---

## 🛠️ Công Cụ VS Code (Tool) Nên Dùng

### 1. **Git Graph** (Khuyên dùng 🌟)
- **Extension:** `mhutchie.git-graph`
- **Tác dụng:** Xem lịch sử commit dạng biểu đồ cây (như bản đồ tàu điện 🚇).
- **Tại sao:** Rất trực quan, dễ thấy rẽ nhánh, merge. Bạn đang dùng cái này rồi!

### 2. **GitLens** (Mạnh mẽ 💪)
- **Extension:** `eamodio.gitlens`
- **Tính năng:**
  - **CodeLens:** Thấy ai sửa dòng code, vào lúc nào ngay trong editor.
  - **File History:** Xem lịch sử thay đổi của 1 file.
  - **Compare:** So sánh code giữa các branch dễ dàng.

### 3. **Source Control** (Có sẵn ⚡)
- **Phím tắt:** `Ctrl + Shift + G`
- **Tác dụng:**
  - **Stage (+):** Chọn file để commit.
  - **Commit:** Ghi lại thay đổi.
  - **Sync:** Nút quay tròn để Push/Pull code nhanh gọn.

