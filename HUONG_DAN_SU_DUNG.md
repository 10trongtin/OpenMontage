# Hướng dẫn sử dụng OpenMontage (tiếng Việt)

OpenMontage là hệ thống làm video bằng AI agent. Bạn mở dự án trong một trợ lý lập trình AI (Claude Code, Cursor, Copilot, Codex...) rồi mô tả video muốn làm bằng lời.

## 1. Cài đặt (làm một lần)

Cần có: Python 3.10+, Node.js 18+ (khuyến nghị 22), FFmpeg.

```bash
git clone https://github.com/10trongtin/OpenMontage.git
cd OpenMontage
make setup          # cài Python deps, Remotion, Piper TTS, HyperFrames, tạo .env
npx hyperframes browser ensure   # tải Chrome headless để render
make preflight      # kiểm tra những công cụ đang dùng được
```

Windows không có `make`: xem mục "No make?" trong README.md.

## 2. Thêm API key (tuỳ chọn)

Mở file `.env` và điền key bạn có. Không có key vẫn chạy được ở chế độ miễn phí (giọng đọc Piper offline, nhạc/ảnh stock miễn phí cần key Pexels/Pixabay).

| Mục đích | Biến trong `.env` |
|---|---|
| Ảnh/video AI | `FAL_KEY`, `GOOGLE_API_KEY`, `REPLICATE_API_TOKEN`, `RUNWAY_API_KEY`, `KLING_API_KEY` |
| Giọng đọc | `ELEVENLABS_API_KEY`, `OPENAI_API_KEY` |
| Ảnh/video stock miễn phí | `PEXELS_API_KEY`, `PIXABAY_API_KEY`, `UNSPLASH_ACCESS_KEY` |
| Nhạc | `SUNO_API_KEY` |

Không bao giờ commit file `.env` (đã nằm trong `.gitignore`).

## 3. Sử dụng

1. Mở thư mục dự án bằng trợ lý AI (ví dụ chạy `claude` trong thư mục này).
2. Gõ yêu cầu, ví dụ:
   - "Làm video 60 giây giải thích cách mạng nơ-ron học."
   - "Làm video 30 giây giới thiệu căn hộ Vinhomes Cần Giờ, giọng đọc tiếng Việt, có phụ đề."
3. Agent sẽ chọn pipeline, nghiên cứu, viết kịch bản, tạo ảnh/giọng/nhạc, dựng và render. Mỗi quyết định sáng tạo đều hỏi bạn duyệt.
4. Video thành phẩm nằm trong thư mục `projects/` (hoặc đường dẫn agent báo).

## 4. Lệnh hữu ích

```bash
make demo-list         # xem các demo có sẵn
make demo              # render demo
make test              # chạy test
make hyperframes-doctor  # kiểm tra môi trường HyperFrames
```

## 5. Tài liệu gốc

`README.md`, `AGENT_GUIDE.md`, `PROJECT_CONTEXT.md`, thư mục `docs/` và `skills/`.
