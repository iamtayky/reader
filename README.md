# EPUB Reader chạy trên GitHub Pages + Google Drive

Đây là website tĩnh đọc file `.epub` trực tiếp trên trình duyệt. Source phù hợp để deploy bằng GitHub Pages.

## Tính năng

- Đọc EPUB bằng `epub.js`.
- Lấy danh sách file `.epub` từ một folder Google Drive public.
- Dark mode.
- Sepia mode / nền giấy.
- Chế độ đọc sách dạng trang.
- Chuyển trang/chapter mượt bằng nút và phím mũi tên.
- Mục lục EPUB.
- Tăng/giảm cỡ chữ.
- Lưu tiến độ đọc, theme và cỡ chữ bằng `localStorage`.
- Fallback mở file EPUB từ máy nếu chưa cấu hình Google Drive.

## Cách dùng nhanh

1. Tạo repository GitHub, ví dụ `epub-reader`.
2. Upload `index.html` lên root của repository.
3. Vào **Settings → Pages**.
4. Chọn **Deploy from a branch**.
5. Branch: `main`, folder: `/root`, sau đó Save.
6. Mở URL GitHub Pages được cấp.

## Cấu hình Google Drive

### 1. Chuẩn bị folder Google Drive

- Tạo một folder trên Google Drive.
- Upload các file `.epub` vào folder đó.
- Share folder ở chế độ **Anyone with the link can view**.
- Copy Folder ID từ link:

```text
https://drive.google.com/drive/folders/FOLDER_ID_NAM_O_DAY
```

### 2. Tạo Google Drive API key

- Vào Google Cloud Console.
- Tạo project mới hoặc dùng project hiện có.
- Enable **Google Drive API**.
- Tạo **API key**.
- Nên giới hạn API key theo HTTP referrer, ví dụ:

```text
https://ten-github-cua-ban.github.io/*
```

### 3. Nhập cấu hình

Cách dễ nhất: mở website, nhập API key và Folder ID ở màn hình đầu tiên, bấm **Lưu cấu hình và tải sách**.

Hoặc điền cố định trong `index.html`:

```js
const DEFAULT_CONFIG = {
  apiKey: "YOUR_GOOGLE_DRIVE_API_KEY",
  folderId: "YOUR_PUBLIC_FOLDER_ID"
};
```

## Lưu ý kỹ thuật

- GitHub Pages chỉ host website tĩnh, không chạy backend riêng.
- Google Drive folder/file phải public nếu không dùng OAuth.
- API key không phải mật khẩu, nhưng vẫn nên giới hạn domain để tránh bị dùng lạm dụng.
- Một số file quá lớn hoặc bị Google Drive chặn tải có thể không mở được trực tiếp.

## Cấu trúc file

```text
.
├── index.html
└── README.md
```
