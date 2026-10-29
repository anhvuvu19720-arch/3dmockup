# Mockup Studio

Web app 3D mockup: chọn mô hình lon, upload label, chỉnh vị trí, xuất PNG.

## Cấu trúc

```
index.html          khung trang + bộ nạp thư viện
css/style.css       giao diện (trắng đen)
js/app.js           toàn bộ xử lý
models/320ml.glb    mô hình lon (BẮT BUỘC, tự thêm)
vendor/             (tuỳ chọn) bản dự phòng của thư viện, xem bên dưới
```

## Chạy trên GitHub Pages

1. Upload toàn bộ thư mục này lên repo (giữ nguyên cấu trúc).
2. Đặt file `320ml.glb` vào thư mục `models/`.
3. Settings → Pages → Deploy from a branch → `main` / root.
4. Mở `https://<tên-github>.github.io/<tên-repo>/`.

Không mở trực tiếp `index.html` từ ổ đĩa: trình duyệt chặn việc tải mô hình. Chạy thử trên máy bằng `python -m http.server` rồi mở `http://localhost:8000`.

## Thêm mô hình mới

1. Đặt file `.glb` vào `models/`.
2. Trong `js/app.js`, tìm `const MODELS=[...]` và thêm một dòng, ví dụ:
   `{name:'Chai 500ml',file:'models/500ml.glb'}`

## Chế độ test mô hình

Thêm `?test=1` vào cuối địa chỉ trang. Tab Model sẽ có nút "Upload .glb to test"; file chỉ nằm trong trình duyệt của bạn. Người dùng bình thường không upload được mô hình.

## Thư viện dự phòng (tuỳ chọn)

Mặc định trang tải Three.js r128 từ CDN. Để chạy không cần mạng ngoài, tải 3 file về và đặt vào `vendor/` với đúng tên:

- `three.min.js` (three r128)
- `OrbitControls.js` (three@0.128.0, examples/js/controls)
- `GLTFLoader.js` (three@0.128.0, examples/js/loaders)

Trang chỉ dùng thư mục này khi CDN không tải được.
