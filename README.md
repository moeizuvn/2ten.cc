# Ihentai API

API cung cấp khả năng tìm kiếm và truy xuất luồng video từ Ihentai.to.

## Base URL
`https://api.2ten.cc`

## API Endpoints

### 1. Tìm kiếm nội dung
**Endpoint**: `GET /i210/search?page={page}&q={query}`

**Tham số**:
- `page` (số, tùy chọn): Số trang, mặc định `1`.
- `q` (chuỗi, tùy chọn): Từ khóa tìm kiếm, để trống để lấy tất cả.

**Phản hồi mẫu**:
```json
{
  "pages": 135,
  "currentPage": 1,
  "query": "",
  "data": [
    {
      "id": "23223",
      "title": "Lewd Bomb Bust Female Teacher - Remaster Edition 1",
      "synopsis": "Cậu học sinh được cô giáo dạy kèm nhưng lại dạy ngược cô.",
      "alternativeTitles": ["淫乱爆乳女教師 MOVIE版 リマスター・エディション"],
      "thumbnail": "https://1.hentaiqq.com/.../Lewd-Bomb-Bust-Female-Teacher-Remaster-Edition-1.jpg",
      "poster": "https://1.hentaiqq.com/.../h-Lewd-Bomb-Bust-Female-Teacher-Remaster-Edition-1.jpg",
      "censorship": "censored",
      "category": "hen3d",
      "languages": ["vi"],
      "updatedAt": "2025-09-27T11:28:32+07:00",
      "createdAt": "2025-09-27T11:28:25+07:00",
      "studios": ["Umemaro 3D"],
      "genres": ["3D", "Big Boobs", "Blow Job", "Gang Bang", "Hiếp dâm", "Megane", "Paizuri", "Stocking", "Teacher"],
      "releaseYear": "2025"
    },
    ...
  ]
}
```

**Mô tả**:
- `pages`: Tổng số trang.
- `currentPage`: Trang hiện tại.
- `query`: Từ khóa tìm kiếm.
- `data`: Mảng kết quả, mỗi đối tượng chứa thông tin chi tiết (ID, tiêu đề, tóm tắt, v.v.).

**Lưu ý**:
- `page` phải là số nguyên dương.
- `q` trống trả về tất cả kết quả.

---

### 2. Lấy luồng video
**Endpoint**: `GET /i210/streams?id={id}`

**Tham số**:
- `id` (chuỗi, bắt buộc): ID của nội dung (VD: `23223`).

**Phản hồi mẫu**:
```json
{
  "data": {
    "streams": [
      "https://play.sonar-cdn.com/watch?v=1e2aca3d-fc30-495b-a559-da1365e4f2db"
    ],
    "m3u8": {
      "480p": "#EXTM3U\n#EXT-X-VE...",
      "720p": "#EXTM3U\n#EXT-X-VE...",
      "1080p": "#EXTM3U\n#EXT-X-VE...",
      "1440p": "#EXTM3U\n#EXT-X-VE..."
    }
  }
}
```

**Mô tả**:
- `data.streams`: Mảng URL luồng video.
- `data.m3u8`: Đối tượng chứa liên kết M3U8 cho các độ phân giải (`480p`, `720p`, `1080p`, `1440p`).

**Lưu ý**:
- `id` phải khớp với ID nội dung từ API tìm kiếm.
- Dữ liệu M3U8 được rút gọn trong mẫu.

## Lưu ý chung
- Tất cả phản hồi đều ở định dạng JSON.
- Đảm bảo xử lý lỗi (VD: kiểm tra `id` hợp lệ, xử lý phân trang).

## Liên hệ
Nếu có thắc mắc, vui lòng mở issue trên GitHub.
